# Replay services

TL;DR:
 - record some set of actions as an interaction sequence and export into a script or sequence that is editable.
 - replay sequence locally ad-hoc on runtimes or connected devices and compare results
 - upload to a test-runner account and select a range of devices & runtime combinations to test against
 - view results of test runs over time, drill down to key tests and metrics
 - trigger test runs on github web hook or similar

### Epic

An app developer starts an  interaction recording session on a FxOS device, starts up an app, then navigates through a specific usage path. When he stops recording, he fetches the recorded set of interactions as a file or chunk of text and saves it.

Once he has the recording open in a text editor he manually edits the start and end bits to ensure that they are ready to replay, then he replays the sequence using the simulator runtime to be sure that what he recorded is exactly what he wants. He then verifies using the original device and a few other phones and tablets lying around.

The replay processes submit timing data to Firefox directly, and he opens the performance dashboard and browses through views including a list of replay runs, detailed views for each replay run as well as comparison graphs across test runs for specific metrics or collections of metrics, for example FPS, CPU, Battery and IO activity.

The replay recording is looking good for his specific test case, so he then logs into the remote replay server, uploads his file and starts a manual test run across the standard 25 device test harness. he then leaves for lunch.

After he comes back from lunch, he reviews the results of the larger test run, ensures it is working as expected and then commits the replay recording to run on each check-in.

The next time a developer checks in code to the repo, github triggers a test run on the replay test harness and this new test runs alongside 500 other tests. The results are viewable via the replay remote dashboard and any failures trigger alerts via email to the developer mailing list.

