# Acceptance testing with Robocorp

## Demo application

The demo application is a very simple login page shown below. With
user name ``demo`` and password ``mode`` you get into a welcome page, and
otherwise you end up to an error page. How to start and stop the
application yourself is explained in the [Starting demo application](#starting-demo-application)
section.

<img src="images/demoapp.png" style="margin-bottom:20px">

## Test Cases

Test case files as well as a resource file used by them are located in
the ``tests`` directory. Click file names below to see the latest versions
online.

[valid_login.robot](tests/valid_login.robot):
    A test suite with a single test for valid login.

    This test has a workflow that is created using keywords in
    the imported resource file.

[invalid_login.robot](tests/invalid_login.robot):
    A test suite containing tests related to invalid login.

    These tests are data-driven by their nature. They use a single
    keyword, specified with the ``Test Template`` setting, that is called
    with different arguments to cover different scenarios.

    This suite also demonstrates using setups and teardowns in
    different levels.

[test.resource](tests/test.resource):
    A resource file with reusable keywords and variables.

    The system specific keywords created here form our own
    domain specific language. They utilize keywords provided
    by the imported [RPA.Browser.Selenium](https://robocorp.com/docs/libraries/rpa-framework/rpa-browser-selenium).

See [Robot Framework cheat sheet](https://robocorp.com/docs/languages-and-frameworks/robot-framework/cheat-sheet) for more details about the test data syntax.

## Running demo

### Starting demo application

Running tests requires the `demo application` located under ``demoapp``
directory to be running.  It can be started either by double clicking
``demoapp/server.py`` file in a file manager or by executing it from the
command line::

    python demoapp/server.py

After the demo application is started, it is be available in URL
`http://localhost:7272`. You can test it manually, valid credentials are
``demo/mode``, and it needs to be running while executing the automated
tests.

If the application was started by double-clicking ``demoapp/server.py``
file, it can be shut down by closing the opened window. If it was
executed from the command line, using ``Ctrl-C`` is enough.

## Running tests

The [test cases](#test-cases) are located in the ``tests`` directory. They can be
executed with `Run Robot` command in Robocorp Lab or Visual Studio Code.

Or using command line with the ``rcc run`` command:

    rcc run -t "Run Test With Firefox"
    rcc run -t "Run Test With Chrome"

### Using different browsers

The browser that is used is controlled by ``TEST_BROWSER`` environment variable defined in
`test.resource` resource file. Firefox browser is used by default.
