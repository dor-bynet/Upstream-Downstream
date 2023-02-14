These two pipelines demonstrate how to trigger downstream jobs from an upstream job, pass parameters to the downstream job, and retrieve the result of the downstream job in the upstream job.

In the first job, "pipeline-triggers-upstream-job," the pipeline script defines a stage "Build" that triggers the second job, "downstream-job," by calling the 'build' function with the job name and three string parameters. After the second job completes, the pipeline script prints the returned value from the downstream job.

In the second job, "downstream-job," the pipeline script defines two stages. In the first stage "Build," the pipeline script sets the environment variable 'RETURNED_VALUE' with a value of "this text is from downstream-job". In the second stage "getting and Printing Artifacts," the pipeline script prints the parameters passed from the upstream job using the 'params' variable.

The first job waits for the second job to complete and then prints the value of the 'RETURNED_VALUE' environment variable set in the second job.

Together, these two pipelines demonstrate how to trigger downstream jobs, pass parameters, and retrieve the result from the downstream job in the upstream job.

