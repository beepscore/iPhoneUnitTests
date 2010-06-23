iPhoneUnitTests

This example illustrates the use of unit tests to ensure that an application’s functionality does not degrade as its source code undergoes changes to improve the application or to fix bugs. The project showcases two types of unit tests: logic and application.

    Logic unit tests allow for stress-testing source code.
    Logic tests are executed as part of the build process to provide
    you with build errors for failed unit tests.
    Logic unit-test bundles are not intented to run in iPhone Simulator or a device.
    A Logic tests target can be built only using the iPhone Simulator SDK.
    
    Application unit tests help ensure the correct linkage between user-interface controls, 
    controller objects, and model objects.
    Application targets with unit tests can be built and run only using the iPhone Device,
    they cannot be built or run using the iPhone Simulator. 

Software requirements
Buildtime: iPhone SDK 3.0 or later.
Runtime:   iPhone OS 3.0 or later.
———————————————————————————————————————————————————————————————————————————————
The iPhoneUnitTests project contains four targets:
- Calc            Builds the Calc application, a simple arithmetic calculator.
- CalculatorTests Builds the CalculatorTests test suite.
- CalcTesting     Builds the Calc application and embeds the CalcTests test suite in it.
- CalcTests       Builds the CalcTests test suite.
———————————————————————————————————————————————————————————————————————————————
Calc Target (app, run in simulator or on device)
The Calc target builds an iPhone application that implements a simple
calculator. The calculating engine is implemented in the Calculator class,
which has two main methods: input: and displayValue.

- input:        This method accepts a one-character string as input.
                This string represents key presses.
- diaplayValue  This method provides the value representing the calculator’s
                output: As each key is pressed, the display value changes,
                as it would on a hardware-based calculator.
———————————————————————————————————————————————————————————————————————————————
CalculatorTests Target (Logic tests, run during build process)

The CalculatorTests target builds a unit-test bundle containing logic tests.
Important: You cannot build or run CalculatorTests using the iPhone Device SDK.
———————————————————————————————————————————————————————————————————————————————
CalcTesting Target (application + application tests, run on device)

The CalcTesting target has a copy of the Calc target, plus the CalcTests test suite.
Its builds the Calc application with the CalcTests test suite embedded into it.
Important: You cannot build or run CalcTesting using the iPhone Simulator SDK.
———————————————————————————————————————————————————————————————————————————————
CalcTests Target (application tests, don't build directly)
The CalcTests target builds a unit-test bundle containing application tests.
You build as part of the target that builds the application to test. In this
case, the CalcTesting target.
Important: Application-tests targets cannot be built directly.
———————————————————————————————————————————————————————————————————————————————
———————————————————————————————————————————————————————————————————————————————
Running CalculatorTests (Logic tests, run during build process)

1. Choose Project > Set Active Target > CalculatorTests.
2. Choose Project > Set Active SDK > iPhone Simulator 3.0 (or later).
3. Choose Build > Build.
   Xcode runs the test cases implemented in the CalculatorTests.m file.
4. Choose Build > Build Results to open the Build Results window, containing
   the tests results. You may have to click the Show Transcript button (the
   third button on the bottom-left corner of the build results list) to view
   the build transcript.
   Alternatively in Build results, set filter to "All Messages",
   click disclosure triangles to expand list,
   then click the icon at the end of the line in the right margin.

The results look similar to this:

   PhaseScriptExecution <project_directory>/build/iPhoneUnitTests.build/Debug-iphonesimulator/CalculatorTests.build/Script-17AA84010F99894F00167681.sh
       cd <project_directory>
       /bin/sh -c <project_directory>/build/iPhoneUnitTests.build/Debug-iphonesimulator/CalculatorTests.build/Script-17AA84010F99894F00167681.sh
   /Developer/Tools/RunPlatformUnitTests.include:364: note: Started tests for architectures 'i386'
   /Developer/Tools/RunPlatformUnitTests.include:371: note: Running tests for architecture 'i386' (GC OFF)
   objc[1222]: GC: forcing GC OFF because OBJC_DISABLE_GC is set
   objc[1222]: GC: forcing GC OFF because OBJC_DISABLE_GC is set
   Test Suite '<project_directory>/build/Debug-iphonesimulator/CalculatorTests.octest(Tests)' started at 2009-05-19 16:55:28 -0700
   Test Suite 'CalculatorTests' started at 2009-05-19 16:55:28 -0700
   <time> otest[1222:80f] -[CalculatorTests testAddition] setUp
   <time> otest[1222:80f] -[CalculatorTests testAddition] start
   <time> otest[1222:80f] -[CalculatorTests testAddition] end
   <time> otest[1222:80f] -[CalculatorTests testAddition] tearDown
   Test Case '-[CalculatorTests testAddition]' passed (0.007 seconds).
   <time> otest[1222:80f] -[CalculatorTests testDivision] setUp
   <time> otest[1222:80f] -[CalculatorTests testDivision] start
   <time> otest[1222:80f] -[CalculatorTests testDivision] end
   <time> otest[1222:80f] -[CalculatorTests testDivision] tearDown
   Test Case '-[CalculatorTests testDivision]' passed (0.003 seconds).
   <time> otest[1222:80f] -[CalculatorTests testInputException] setUp
   <time> otest[1222:80f] -[CalculatorTests testInputException] start
   <time> otest[1222:80f] -[CalculatorTests testInputException] end
   <time> otest[1222:80f] -[CalculatorTests testInputException] tearDown
   ...
   Test Case '-[CalculatorTests testSubtractionNegativeResult]' passed (0.002 seconds).
   Test Suite 'CalculatorTests' finished at 2009-05-19 16:55:28 -0700.
   Executed 6 tests, with 0 failures (0 unexpected) in 0.021 (0.022) seconds

   Test Suite '<project_directory>/build/Debug-iphonesimulator/CalculatorTests.octest(Tests)' finished at 2009-05-19 16:55:28 -0700.
   Executed 6 tests, with 0 failures (0 unexpected) in 0.021 (0.024) seconds

   /Developer/Tools/RunPlatformUnitTests.include:388: note: Passed tests for architecture 'i386' (GC OFF)
   /Developer/Tools/RunPlatformUnitTests.include:399: note: Completed tests for architectures 'i386'

———————————————————————————————————————————————————————————————————————————————
Running CalcTesting Application Tests

1. Choose Project > Set Active Target > CalcTesting.
2. Choose Project > Set Active SDK > iPhone Device 3.0 (or later).
3. Choose Build > Build and Run. Xcode builds the target, installs
   the application on your device, launches the application, runs the tests,
   and terminates the application.
4. Choose Run > Console to open the Console window, containing
   the test results.

The application-tests results look similar to this:

   Test Suite 'All tests' started at 2009-05-19 16:17:18 -0700
   Test Suite '/Developer/Library/Frameworks/SenTestingKit.framework(Tests)' started at 2009-05-19 16:17:18 -0700
   Test Suite 'SenInterfaceTestCase' started at 2009-05-19 16:17:18 -0700
   Test Suite 'SenInterfaceTestCase' finished at 2009-05-19 16:17:18 -0700.
   Executed 0 tests, with 0 failures (0 unexpected) in 0.000 (0.009) seconds

   Test Suite '/Developer/Library/Frameworks/SenTestingKit.framework(Tests)' finished at 2009-05-19 16:17:18 -0700.
   Executed 0 tests, with 0 failures (0 unexpected) in 0.000 (0.031) seconds

   Test Suite '/var/mobile/Applications/B808F084-EF94-42B3-AB2E-1B1938690AE1/Calc.app/CalcTests.octest(Tests)' started at 2009-05-19 16:17:18 -0700
   Test Suite 'CalcTests' started at 2009-05-19 16:17:18 -0700
   Test Case '-[CalcTests testAddition]' passed (0.008 seconds).
   Test Case '-[CalcTests testAppDelegate]' passed (0.000 seconds).
   Test Case '-[CalcTests testClear]' passed (0.010 seconds).
   Test Case '-[CalcTests testDelete]' passed (0.006 seconds).
   Test Case '-[CalcTests testDivision]' passed (0.004 seconds).
   Test Case '-[CalcTests testMultiplication]' passed (0.004 seconds).
   Test Case '-[CalcTests testSubtraction]' passed (0.003 seconds).
   Test Suite 'CalcTests' finished at 2009-05-19 16:17:18 -0700.
   Executed 7 tests, with 0 failures (0 unexpected) in 0.035 (0.077) seconds

   Test Suite '/var/mobile/Applications/B808F084-EF94-42B3-AB2E-1B1938690AE1/Calc.app/CalcTests.octest(Tests)' finished at 2009-05-19 16:17:18 -0700.
   Executed 7 tests, with 0 failures (0 unexpected) in 0.035 (0.097) seconds

   Test Suite 'All tests' finished at 2009-05-19 16:17:18 -0700.
   Executed 7 tests, with 0 failures (0 unexpected) in 0.035 (0.168) seconds


SB got
warning: Couldn't get real path for inserted library /Developer/Platforms/iPhoneOS.platform/DeviceSupport/4.0 (8A293)/Symbols/Developer/Library/PrivateFrameworks/DevToolsBundleInjection.framework/DevToolsBundleInjection
searched and found
http://stackoverflow.com/questions/1713280/linker-error-iphone-unit-test-bundle-referencing-app-classes

———————————————————————————————————————————————————————————————————————————————
Related Information
For more information, see the “Unit Testing iPhone Applications” chapter in
iPhone Development Guide.

Copyright © 2009 Apple Inc. All rights reserved.


