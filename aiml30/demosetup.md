# Demo Setup
Follow the below steps to get your environment ready for the live demo. Once you complete this setup then follow the [demo guide](demoguide.md).

## Create Azure Machine Learninge Resources with the Deploy to Azure Button below
<a href="https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fcassieview%2Fignite-learning-paths-training-aiml%2Fmaster%2Faiml30%2Fdeploy.json" rel="nofollow">
 <img src="https://camo.githubusercontent.com/9285dd3998997a0835869065bb15e5d500475034/687474703a2f2f617a7572656465706c6f792e6e65742f6465706c6f79627574746f6e2e706e67" data-canonical-src="http://azuredeploy.net/deploybutton.png" style="max-width:100%;">
</a>

> Once created please upgrade your Azure Machine Learning resource to the enterprise edition for this session. You should see an 'Upgrade' button to complete this action. This is currently in preview, however the pricing structure is described [here](https://azure.microsoft.com/en-us/pricing/details/machine-learning/)

## Create Additional Resources Needed

* Select **'Launch the new Azure Machine Learning studio'**

Once you have created the base Azure Machine Learning Service we need to add additional compute resources.
### Create Compute Targets
1. Create Machine Learning Compute
    * Click on the nav "Compute"
    * Select 'Training Clusters'
    * Click "New"
    * Enter a name for the resource
    * Select the machine size (ex: Standard_DS2_v2)
    * Enter the min and max nodes (recommend min of 0 and max of 5)
    * Click "Create"
    ![Create Compute](https://globaleventcdn.blob.core.windows.net/assets/aiml/aiml30/CreateMlCompute.gif)
2. Create Kubernetes Compute
    * Click on the nav "Compute"
    * Select 'Inference Clusters'
    * Click "New"
    * Enter a name for the resource
    * Select a region
    * Keep 'Virtual Machine Size' as default
    * Cluster purpose set to 'Dev-test'
    * Click "Create"
    ![Create Kubernetes](https://globaleventcdn.blob.core.windows.net/assets/aiml/aiml30/CreateKubService.gif)
3. Create Notebook Virtual Machine
    * Click on the NAV "Compute"
    * Select 'Notebook VMs'
    * Click "New"
    * Give the notebook a unique name
    * Select the VM size
    * Click "Create"
    ![Create VM](https://globaleventcdn.blob.core.windows.net/assets/aiml/aiml30/CreateNotebookVM.gif)


## Upload Dataset to Workspace Blob Storage and Save to Local
The dataset needed is created weekly with updated dates to allow your demo to be predicting future weeks. Below are the steps to get the new dataset and add it to the Azure Machine Learning Storage account and the demo data app.

1. Download dataset to local from [here](https://globaleventcdn.blob.core.windows.net/assets/aiml/aiml30/datasets/ForecastingData.csv)
2. Open Azure Storage Explorer - [Download Here](https://azure.microsoft.com/en-us/features/storage-explorer/).
3. Navigate to `azureml-blobstore-<guid>`
4. Create a new folder called `datasets`
5. Upload the dataset
6. Replace local ForecastingData.csv file in the C# Demo app in order to be predicting for future dates. There is a default csv however it will not be the updated data.

## Get the C# Demo App
The first demo is with VS Code and the C# IgniteAimlDataApp. This is to demonstrate how to do the data processing and highlight that the it can be done in any language.

1. [Download VS Code here](https://code.visualstudio.com/download)
2. Ensure that you have [.NET Core SDK 2.1.0](https://dotnet.microsoft.com/download/dotnet-core/2.1) installed on your local
3. Clone the app with the following command
    * `git clone https://github.com/microsoft/ignite-learning-paths-training-aiml.git`
4. Navigate to project path
    * `cd ignite-learning-paths-training-aiml/aiml30/C#/IgniteAimlDataApp/IgniteAimlDataApp`
5. Open the project in VS Code
    * `code .`
6. Replace the local dataset with the downloaded dataset from the step above in the `IgniteAimlDataApp/Datasets` Folder.
7. To run the app
    * Right click on `Program.cs` and select `Open in Terminal`
    * Run the command `dotnet run`
    * It will prompt with a question `Would you like to run the default params` type `y`
    * This will attempt to hit the API but it will fail since it hasn't been created yet.

## Run through the Live Demo
Do a complete run through of the live demo to have a completed backup model to open and show the end result.

#### There will not be enough time to run the model during the live demo. Make sure to build the model _without_ running it in the live session. Once you have added all the modules to the experiment workspace then navigate to the model you created and trained prior to the session.

[Next - Live Demo Steps](demoguide.md)
