
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

## Deal with content in bundle [[Ref]](http://www.programcreek.com/java-api-examples/org.eclipse.core.runtime.FileLocator)

1. Example 1 
```Java
/**
 * Unlike the other supported DB engines, the MySQL JDBC driver ships with
 * the AWS Toolkit for Eclipse.
 *
 * We copy the library out of the plugin directory because as new plugin
 * versions are installed, this location could become invalid once new
 * plugin versions replace this version and have a different path on disk.
 *
 * @return The file where the MySQL driver library was installed in the
 *         workspace.
 */
private File installMySqlDriverInWorkspace() {
    Bundle bundle = Platform.getBundle(RDSPlugin.PLUGIN_ID);
    Path path = new Path("lib/" + MYSQL_DRIVER_FILE_NAME);
    URL fileURL = FileLocator.find(bundle, path, null);

    try {
        IPath stateLocation = Platform.getStateLocation(Platform.getBundle(RDSPlugin.PLUGIN_ID));
        File mysqlDriversDir = new File(stateLocation.toFile(), "mysqlDrivers");

        String jarPath = FileLocator.resolve(fileURL).getPath();
        File sourceFile = new File(jarPath);
        File destinationFile = new File(mysqlDriversDir, MYSQL_DRIVER_FILE_NAME);

        FileUtils.copyFile(sourceFile, destinationFile);
        return destinationFile;
    } catch (IOException e) {
        throw new RuntimeException("Unable to locate MySQL driver on disk.", e);
    }
}
```

2. Example 2

```Java
@Override
protected void initializeImageRegistry(ImageRegistry reg) {
	for (Image image : Image.values()) {
		Bundle bundle = Platform.getBundle(ID_PLUGIN);
		IPath path = new Path("icons/" + image.getPath());
		URL url = FileLocator.find(bundle, path, null);
		ImageDescriptor desc = ImageDescriptor.createFromURL(url);
		reg.put(image.name(), desc);
	}
}
```

3. Example 3 [[Ref]](http://stackoverflow.com/questions/5756218/eclipse-ide-plugin-development-copy-files-from-plugin-jar-to-active-project-fol)

```Java
Bundle bundle = Platform.getBundle( "your.plugin.id" );
InputStream stream = FileLocator.openStream( bundle, "path.in.plugin", false );
IProject project = ResourcesPlugin.getWorkspace().getRoot().getProject( "your.project" );
IFile file = project.getFile( "something/abc.txt" );
file.create( stream, true, null );
``` 

## File Path String to IFile [[Ref]](http://stackoverflow.com/questions/960746/how-to-convert-from-file-to-ifile-in-java-for-files-outside-the-project)
Works for the file in  workspace
```Java
IWorkspace workspace= ResourcesPlugin.getWorkspace();    
IPath location= Path.fromOSString(file.getAbsolutePath()); 
IFile ifile= workspace.getRoot().getFileForLocation(location);
```