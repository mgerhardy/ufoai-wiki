Some code cleanup is needed as well as finishing some currently
unfinished features.

- remove baseCurrent assignments from every place except base selecting
  (taken by [Zenerka](User:Zenerka "wikilink"))

  - See also [TODO/2.2/baseCurrent](TODO/2.2/baseCurrent "wikilink") for
    a summary on the situation and some hints on what is needed.

<!-- -->

    src/client/cl_aircraft.c:                                                       baseCurrent = aircraft->homebase;
    src/client/cl_main.c:           baseCurrent = &gd.bases[0];
    src/client/cl_popup.c:  baseCurrent = aircraft->homebase;
    src/client/cl_basemanagement.c: baseCurrent = &gd.bases[baseID];
    src/client/cl_basemanagement.c:                 baseCurrent = &gd.bases[baseID];
    src/client/cl_basemanagement.c:                 baseCurrent = &gd.bases[0];
    src/client/cl_basemanagement.c:         baseCurrent = &gd.bases[baseID];
    src/client/cl_basemanagement.c:         baseCurrent = b;
    src/client/cl_campaign.c:       baseCurrent = aircraft->homebase;
    src/client/cl_campaign.c:       baseCurrent = aircraft->homebase;
    src/client/cl_campaign.c:       baseCurrent = AIR_AircraftGetFromIdx(gd.interceptAircraft)->homebase;
    src/client/cl_campaign.c:       baseCurrent = NULL;
    src/client/cl_basesummary.c:    baseCurrent = NULL;

- replace int baseidx in Alien Containment function calls with base
  pointer (taken by [Zenerka](User:Zenerka "wikilink"))

- handling a mission, the aircraft should be selected by comparing
  aircraft-\>mission with selected mission - remove every baseCurrent,
  baseCurrent-\>aircraftCurrent usage (see
  [baseCurrent](TODO/2.2/baseCurrent "wikilink") for more), fix team
  selection (taken by [Zenerka](User:Zenerka "wikilink"))

- clean a mess with assigning employees to buildings and removing them

  - cl_basemanagement.c/B_HireForBuilding()

  - cl_employee.c/E_AssignEmployeeToBuilding() (currently commented out)

  - cl_employee.c/E_RemoveEmployeeFromBuilding()

- destroying building (cl_basemanagement.c/B_BuildingDestroy()) should:

  - update capacities

  - remove/update personel from building (in case of worker or
    scientist)

  - remove/update aliens for B_ALIEN_CONTAINMENT (taken by
    [Zenerka](User:Zenerka "wikilink"))

  - remove/update items for B_STORAGE - not so easy, because equipment
    being used by soldiers in teams is still stored in storage too; that
    needs to be changed first, see [Inventory to team
    assignment](TODO/2.2#Inventory_to_team_assignment "wikilink") TODO
    entry

  - remove antimatter for B_ANTIMATTER

- rename all armor variables to armour - hoehrer started this already

- (try to) merge nameCat and teamDesc arrays - store all info about
  given character type in one array

- merge craftitems with struct objDef_s - thanks to that no new code
  will be needed for producing, purchasing, transfering, selling,
  disassembling, storing subsystems

[Category:Contribute](Category:Contribute "wikilink")
[Category:TODO](Category:TODO "wikilink")
[Category:Development](Category:Development "wikilink")