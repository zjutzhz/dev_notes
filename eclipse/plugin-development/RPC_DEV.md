
## Get the selected project [[Ref]](http://stackoverflow.com/questions/6892294/eclipse-plugin-how-to-get-the-path-to-the-currently-selected-project)
```Java
    IWorkbenchWindow window = PlatformUI.getWorkbench().getActiveWorkbenchWindow();
    if (window != null)
    {
        IStructuredSelection selection = (IStructuredSelection) window.getSelectionService().getSelection();
        Object firstElement = selection.getFirstElement();
        if (firstElement instanceof IAdaptable)
        {
            IProject project = (IProject)((IAdaptable)firstElement).getAdapter(IProject.class);
            IPath path = project.getFullPath();
            System.out.println(path);
        }
    }
```