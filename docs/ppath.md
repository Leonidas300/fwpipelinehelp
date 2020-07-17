# Getting Pipeline Path

Fist we check if user select any pipeline.

```C#

using FWPipelineSDK.IO;

//...//your code

if(EnvironmentVariableManager.CheckRegistryForVariable("FWCurrentPipeline", false))
{
    // Your code here...
}
```
The first variable is a name of the environment variable we looking for, second is user scope and it is `false` becouse we want pc variables.
Then we gonna get the piepline variable.

```C#
var pipeline = EnvironmentVariableManager.GetEnvironmentVariableFromTarget("FWCurrentPipeline", EnvironmentVariableTarget.Machine);
```

Next we need to get the actual path.

```C#

var path = FWProject.GetPipelinePath(pipeline); //The actual full path to the pipeline

```

The hole code looks like this:

```C#

using FWPipelineSDK.IO;

namespace test{

    class test{

        public void ShowPath()
        {
            if(EnvironmentVariableManager.CheckRegistryForVariable("FWCurrentPipeline", false))
            {
                var pipeline = EnvironmentVariableManager.GetEnvironmentVariableFromTarget("FWCurrentPipeline", EnvironmentVariableTarget.Machine);
                
                var path = FWProject.GetPipelinePath(pipeline);
                
                Console.WriteLine(path);

            }
        }
    }
}
```