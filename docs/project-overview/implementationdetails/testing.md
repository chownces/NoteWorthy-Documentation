# Implementation Details

### Testing
**Unit tests** are important in all software engineering projects. A properly written set of tests is
vital in ensuring the 'correctness' of the program without manually checking each function and
edge cases whenever there are changes or additions to the codebase.

Although it might be a hassle to set up initially, unit tests are akin to long-term investments, and
grant both cost and time savings as the piece of software continues to scale and grow.

Below is a summary of the testing suite employed in this project.

##### Jest
As both our frontend and backend were written in JavaScript, *Jest* was the obvious testing framework to use,
with its good documentation and ease of use.

#### Frontend
On the frontend, we mocked our GraphQL queries and used <u>snapshot testing</u> as our primary test suite. Snapshot
testing, when done properly, is a useful tool for testing frontend code, as it ensures that our UI does not
change unexpectedly.

> "A typical snapshot test case renders a UI component, takes a snapshot, then compares it to a reference snapshot
> file stored alongside the test. The test will fail if the two snapshots do not match: either the change is
> unexpected, or the reference snapshot needs to be updated to the new version of the UI component."
>
> <div style="text-align: right">*~ A brief explanation of snapshot testing by Jest*</div>

#### Backend
As we were using GraphQL as opposed to the traditional RESTful API which uses route handlers, our <u>unit tests</u> were
done around the <u>GraphQL resolvers</u>. Unfortunately, the documentation surrounding GraphQL resolver testing is still quite
limited, and we spent a longer time than expected to get it working.

Ultimately, we used `mongodb-memory-server` to start up an in-memory MongoDB test database which we seeded, and used Apollo Server's
built-in `executeOperation` method to run unit tests against our resolvers.

#### Extensions
Due to the limited project timeframe and manpower, we settled with snapshot testing and backend unit tests. If we had more
time, we would have looked into end-to-end testing and also defining a set of manual tests to validate our UI/UX.