## The Design

The design idea is to create a continuous integration and continuous delivery using AWS services.

The main flow will be:

```
  |-> build triggered by push (or pull request)
  |---> Suite of tests
  |----> Merge the commit
  |-----> Regression/more tests
  |------> Deploy as a new release.
```

If any tests or stages fail, everything is aborted and discarded, following a Blue/Green deployment type.

## Components
This would be achieved using AWS Code Pipeline to trigger a build upon a pushed commited.

After the build is completed successfully, the pipeline moves to the testing phase.

After all testing is completed on this branch, it will then merge the code and run some other test cycle.

If all that is passed, it will then go ahead and put that change into production and deploy the final version of the application.

## Thinking Process

The implementation approach I took was from simplest to more complex. This has many benefits, as you can catch and solve bugs as soon as they are introduced.

The tools are EC2, S3 for the instances, CodeBuild and CodeDeploy, along with CodePipeline in the end.
