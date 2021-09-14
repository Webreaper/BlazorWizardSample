# BlazorWizardSample
 Sample of an approach to build a Wizard in Blazor, written to demonstrate how Blazor is easy. Total development time, 38 mins.

<img src="./WizardSample.gif">

General principals: 
* The data model for all steps of the Wizard is defined here in [WizardModel.cs](https://github.com/Webreaper/BlazorWizardSample/blob/main/BlazorWizardSample/Data/WizardModel.cs).
* The Wizard page defines an instance of the model as a Cascading Value that will be passed down to all child controls:

```HTML
<CascadingValue Value="Model">
    <WizardContainer />
</CascadingValue>
```
* The `WizardContainer` manages the Step state, and is responsible for displaying/hiding the steps other than the current one, as well as displaying the model's final state when the Wizard completes.
* The [Wizard steps](https://github.com/Webreaper/BlazorWizardSample/tree/main/BlazorWizardSample/Shared/WizardSteps) are defined as 3 components, each of which accesses the model instance via a Cascading parameter, and then binds to the properties in the model as normal with Blazor.\

It would be possible to make the `WizardContainer` even simpler - it could take a collection of `WizardStep` render fragments and process them dynamically, but unless there's a particularly complex set of paths through the wizard, this is probably overkil.
