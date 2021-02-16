# Omnifocus Dependency Plugin
![demo](demo.gif)

- multi-to-multi dependency setup.
- Projects and tasks can depend on each other.
- Noninvasive, will not modify the original task. Only two extra tags required.

## Install
Open `dependency-setup.omnijs` with omnifocus.

## Configuration
The plugin requires 2 tags:
- `Dependency`: used to mark tasks as dependency
- `Depend On`: when create dependency, plugin will create a special action with this tag.   
After dependency actions completed, this action will auto complete.

If want to use your own tags instead, change these two functions to return your tag:
```js
var dependencyTag = function () {
    return tagNamed("Dependency")
}
var dependOnTag = function (){
    return tagNamed("Task").tagNamed("Depend On")
}
```

## Usage

### Setup dependency: task A depend on B

For example, you want to mark action B depend on action A, which means A is not available until B completed.

1. Mark task B with tag `Dependency`
2. Select task A and run plugin
3. A Form will come up with dependency info. These actions are either actions tagged with `Dependency` or existed 
dependency tasks. Select / unselect dependency tasks you want and press `Go`. Default all selected.
4. A task tagged with `Depend on` will be created as a child of task A. So task A will not be available until its children completed.
`Dependency` tag on task A was also being removed.

### Dependency on complete: task A become available after task B is done.

1. After the task B is complete, run plugin again
2. An Alert will pop up and tell you that task A is now available.

### Dependency Management
You can add or remove dependency tasks. If you want to add dependency task, tag dependency tasks with `Dependency` first.
Then follow [Setup dependency](#setup-dependency-task-a-depend-on-b) to select/unselect dependency tasks that you want to add/remove.

### Auto cleanup

The `Auto Complete` check box in form decides if `Dependency` tag will be removed after setup dependency task.

If `Auto Complete` is selected (default), after some tasks had been set to depend on the actions with `Dependency` tag, 
`Dependency` tag will be removed from these dependency tasks.   
If `Auto Complete` is unselected, `Dependency` tags will not be remove after setup dependency task.

This is useful when multiple tasks in different project depend on one task. It is more convenient than tag actions again and again.