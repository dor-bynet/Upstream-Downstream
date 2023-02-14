These two pipelines demonstrate how to trigger downstream jobs from an upstream job, pass parameters to the downstream job, and retrieve the result of the downstream job in the upstream job.

In the first job, "pipeline-triggers-upstream-job," the pipeline script defines a stage "Build" that triggers the second job, "downstream-job," by calling the 'build' function with the job name and three string parameters. After the second job completes, the pipeline script prints the returned value from the downstream job.

![image](https://user-images.githubusercontent.com/123317116/218687103-1fed7731-2ca7-4163-8700-bb16d9a0951d.png)

In the second job, "downstream-job," the pipeline script defines two stages. In the first stage "Build," the pipeline script sets the environment variable 'RETURNED_VALUE' with a value of "this text is from downstream-job". In the second stage "getting and Printing Artifacts," the pipeline script prints the parameters passed from the upstream job using the 'params' variable.

The first job waits for the second job to complete and then prints the value of the 'RETURNED_VALUE' environment variable set in the second job.

Together, these two pipelines demonstrate how to trigger downstream jobs, pass parameters, and retrieve the result from the downstream job in the upstream job.


- - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - 


The commented out "triggers" section in the second pipeline script is an alternate way of triggering the downstream job "pipeline-triggers-upstream-job" when the upstream job "downstream-job" succeeds. This approach is known as defining upstream and downstream projects, and it allows Jenkins to automatically start the downstream job when the upstream job completes successfully.

![image](https://user-images.githubusercontent.com/123317116/218682628-ea0230fe-fb06-4435-9da4-2a8bf45c9c0a.png)

In this example, the 'threshold' parameter is set to "SUCCESS" to indicate that the downstream job should only be triggered when the upstream job completes successfully. This approach provides a more streamlined and automated solution for triggering downstream jobs and is useful in larger, more complex pipelines.

Using this method, you will also need to configure upstream and downstream jobs using the Jenkins GUI, you would need to navigate to the "Configure" page of the downstream job and add under Build Triggers" > "build after other projects are build" > "projects to watch > and add the upstream job. 
Once configured, the downstream job will be automatically triggered when the upstream job completes successfully.

![image](https://user-images.githubusercontent.com/123317116/218689254-0fa9fcd0-77c7-433e-9b1b-1a147497485d.png)
