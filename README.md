# UCCs-and-City-Toll-Schemes-Problem-Instances-and-Solution-Summary

**Reference:** *"Urban Consolidation Centers and City Toll Schemes – Investigating the Impact of City Tolls on Transshipment Decisions"*
**Problem variant:** *Multi-trip multi-path fleet size and mix vehicle routing problem with time windows and transshipment facilities (MTMP-FSMTWTF)*

## Solution File Description

Each row of the *solution_summary.csv* file corresponds to the best solution found for the factor level combination.

experimentId			= unique id for the factor level combination  
instanceName			= name of the corresponding instance file  
  
  
|**Factors**		|		**Levels**|
| --- | --- |
|studyRegion 		|	{Milan, London, Ruhr}|
|averageDemand (q)	|	{1.5, 3}|
|shareCustomersInTollZones|	{20%, 40%}|
|cUCC		|		{2, 4, 6, 8, 10}|
|cToll (cτ)		|	{0, 5, 10, 15, 20}|
|tollType		|	{none, per_day, per_entrance}|

**Output metrics:**
|**Metric** | **Description**|
| --- | ------- |
|sumTotalCost		|	 sum of total costs |
|sumUCCCost		|	sum of UCC usage costs|
|qUsageUCC		|	sum of demand transshipped to UCCs|
|numUCCUsage		|	=number of customer requests transshipped to UCCs|
|uCCUsagePercent	|		percentage of customer requests transshipped to UCCs|
|numTrucksInTollArea	|	 numer of vehicles that enter a toll area at least once|
|numMediumTrucks			 |number of medium-trucks used in the solution|
|numLargeTrucks			|number of large-trucks used in the solution|
|sumTollCost			|sum of toll costs|
|numTollAreaTruckEntries		| number of truck entries into toll zones |

## Instance File Description

Each instance file consists of four excel sheets. In the following an overview is given of each sheet and its columns.

**Distanz-Zeit-Matrix:** Contains a time-distance matrix with distance and travel time between every two locations.  
*-from_loc:* location_Index of the *"from"* location  
*-to_loc:* location_Index of the *"to"* location.  
*-distance:* distance in kilometers between the *"from"* and to *"location"*.  
*-travel_time:* driving time in minutes between the *"from"* and to *"location"*.   
*-path_index:* index of the path between the two locations.  
*-in_toll_area_X:* indicates whether the toll area *X* is accessed by the path.  

**Services:** contains information regarding customer requests.  
*-job_id:* name of customer requests. Can be ignored.  
*-volume:* quantity of customer requests.  
*-locations:* list of location indices to which a customer request can be delivered.  
*-service_time_var:* location-independent service time per customer request.  

**Locations:** contains information regarding the locations.  
*-name:* location name (can be ignored).  
*-tw_start:* time window start.  
*-tw_end:* time window end.  
*-type:* location type (Customer, DEPOT, UCC, or INTERMEDIATE_DEPOT).  
*-location_Index:* index to match locations with customer requests  
*-x_coord and y_coord:* coordinates of locations. Not used in the instances provided here.  
*-service_time_fix:* location-dependent preparation time.  
*-toll_area:* indicates in which toll area(s) a location is.  

**Meta-Info:** contains general information on the instance.  
*-num_toll_areas:* number of toll areas.  
*-max_num_paths:* maximum number of paths non-dominated paths between two vertices.  
*-num_routing_profiles:* can be ignored for the problems discussed in this paper.  
*-num_locations:* the total number of locations.  
*-num_transshipment_facilities:* total number of transshipment facilities (UCCs).  
*-problem_type:* label to indicate the problem type and thus transshipment cost type (real = per volume)  
  
vehicle information list: Each row corresponds to one vehicle type.  
*-vehicle_name:* name of the vehicle of that row (can be ignored).  
*-num_vehicles* = number of available vehicles for that type.  
*-vehicle_capacity*  
*-cost_per_distance*  
*-cost_per_time:* duration-dependent cost.  
*-fixed_cost:* fixed cost per vehicle use.  
*-toll_cost_factor:* a factor to modify the toll costs of a vehicle (always set to 1 in the provided instance files).  
*-latest_arrival:* maximum allowable shift duration of the vehicle.  
*-distance_metric:* distance metric used to calculate the distances (always uses the time-distance-matrix the provided instance files).  
