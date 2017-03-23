# SimpleGapRule
Simple campsite gap rule implementation in Nova

__The problem__

 > Most destination resorts don’t host guests who are willing to stay for only one night. Their guests are not simply passing through the area; they’ve often travelled far with lots of luggage specifically to stay there, and it’s not worth it for them to stay one night. As a result, a reservation system for resorts needs to prevent one night gaps in its reservation grid, or schedule of inventory. If one-night gaps occur on the grid, they will not be sold, and this results in lost income for the resort owner. For example, Campspot uses a one-night gap rule, as this is a common problem for camping resort owners. However, owners’ gap problems aren’t limited to one-night gaps. Some resorts only host guests who stay a minimum three or four nights. Those resorts may want to prevent one-, two-, and three-night gaps.

__The algorithm__

Given a search time interval, to validate that the search interval does not violate the gap rule, the program will do the following for each campsite:

 1. Get the campsite's reservation times that are adjacent to the given search time interval.
    1. An adjacent interval does not overlap the search time interval
    2. An adjacent interval has the least absolute distance from the search interval compared to all other intervals on the side that the current interval of interest is located.
 2. Validate that the distance between each adjacent reservation interval and the search interval is not equal to a specified gap rule.

If both points are valid, then the search time is available for the tested campsite.

__Assumptions__

 * Check the given gap rules exactly; no less than. (e.g. if only gap rule is 3 days, then 1 and 2 are valid)
 * The json input files are formatted correctly (including valid property values, e.g. valid dates).
 * Quotes were intended to surround the outputted campsite names.
 * "Teddy *Rosevelt* Tent Site" was a typo in the test-case.json (I did not fix) 

__Running the project from command line__

Open command line and navigate to the root project directory.

If you are running on Windows, run the `SimpleGapRule test-case.json` command.

If you are running on Mac, run the `./SimpleGapRule test-case.json` command.

__Running the unit tests from command line__

Open command line and navigate to the root project directory.

If you are running on Windows, run the `SimpleGapRuleTests` command.

If you are running on Mac, run the `./SimpleGapRuleTests` command.

The output should resemble:

    ============================== Testing ModelTests ==============================
    Testing searchDate - Success
    Testing campsiteCount - Success
    Testing reservationCount - Success
    Testing gapRuleCount - Success
    Testing campsiteContent - Success
    Testing reservationContent - Success
    Testing gapRuleContent - Success

    ============================= Testing GapRuleTests =============================
    Testing givenTestCase - Success
    Testing noOpenings - Success
    Testing noReservations - Success
    Testing singleReservationConflict - Success

    ============================ Testing FileInputTests ============================
    Testing allTestCasesCount - Success
    Testing folderTestCasesCount - Success
    Testing singleFileTestCasesCount - Success
    Testing nonExistentFile - Success
    Testing folderWithNoJson - Success

    :) :) :) :) :) :) :) :) :) :) :) All Successful  (: (: (: (: (: (: (: (: (: (: (