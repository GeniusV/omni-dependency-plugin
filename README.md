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
3. A Form will come up with dependency info
4. A task tagged with `Depend on` will be created as a child of task A. So task A will not be available until its children completed.
 
### Dependency on complete: task A become available after task B is done.

1. After task B is complete, run plugin again
2. An Alert will pop up and tell you that task A is now available.

### Dependency Management

### Auto cleanup
