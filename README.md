Exterminator is a system process killer written in Python and Elementary

Radiance Theme:
![alt text](https://raw.githubusercontent.com/JeffHoogland/exterminator/master/screenshot/exterminator.png "Exterminator") 

Default Theme:
![alt text](https://raw.githubusercontent.com/JeffHoogland/exterminator/master/screenshot/exterminator-default.png "Exterminator")


Tested with:

- Python3.9
- Python-efl 1.25.0
- Elmextentions Python3 v 0.3.1rc.0
- Other libs as in requirements.txt

Credits: 
- [Jeff Hoogland](http://www.jeffhoogland.com/)
- [SRP0706](https://github.com/srp0706/)
- [Abdur-Rahmaan Janhangeer](https://www.compileralchemy.com)


# Conventions

Name widget variables after the efl widget name like `ram_progress_bar`

Use self. if in a class


# Docs

## Scroller

A scroller holds a single object and “scrolls it around”.

This means that it allows the user to use a scrollbar (or a finger) to drag the viewable region around, allowing to move through a much larger object that is contained in the scroller. The scroller will always have a small minimum size by default as it won’t be limited by the contents of the scroller.

This widget inherits from LayoutClass, so that all the functions acting on it also work for scroller objects.

## Box

A box arranges objects in a linear fashion, governed by a layout function that defines the details of this arrangement.

By default, the box will use an internal function to set the layout to a single row, either vertical or horizontal. This layout is affected by a number of parameters, such as the homogeneous flag set by homogeneous, the values given by padding and align and the hints set to each object in the box.

For this default layout, it’s possible to change the orientation with horizontal. The box will start in the vertical orientation, placing its elements ordered from top to bottom. When horizontal is set, the order will go from left to right. If the box is set to be homogeneous, every object in it will be assigned the same space, that of the largest object. Padding can be used to set some spacing between the cell given to each object. The alignment of the box, set with align, determines how the bounding box of all the elements will be placed within the space given to the box widget itself.

The size hints of each object also affect how they are placed and sized within the box. size_hint_min will give the minimum size the object can have, and the box will use it as the basis for all latter calculations. Elementary widgets set their own minimum size as needed, so there’s rarely any need to use it manually.

size_hint_weight, when not in homogeneous mode, is used to tell whether the object will be allocated the minimum size it needs or if the space given to it should be expanded. It’s important to realize that expanding the size given to the object is not the same thing as resizing the object. It could very well end being a small widget floating in a much larger empty space. If not set, the weight for objects will normally be 0.0 for both axis, meaning the widget will not be expanded. To take as much space possible, set the weight to EVAS_HINT_EXPAND (defined to 1.0) for the desired axis to expand.

Besides how much space each object is allocated, it’s possible to control how the widget will be placed within that space using size_hint_align. By default, this value will be 0.5 for both axis, meaning the object will be centered, but any value from 0.0 (left or top, for the x and y axis, respectively) to 1.0 (right or bottom) can be used. The special value EVAS_HINT_FILL, which is -1.0, means the object will be resized to fill the entire space it was allocated.

In addition, customized functions to define the layout can be set, which allow the application developer to organize the objects within the box in any number of ways.

The special Box.layout_transition() function can be used to switch from one layout to another, animating the motion of the children of the box.

## Panes

The panes widget adds a draggable bar between two contents. When dragged this bar will resize contents’ size.

Panes can be displayed vertically or horizontally, and contents size proportion can be customized (homogeneous by default).

## StandardWindow

Python. This creates a window like Window but also puts in a standard Background, as well as setting the window title to title. The window type created is of type ELM_WIN_BASIC, with None as the parent widget.

## Progressbar

The progress bar is a widget for visually representing the progress status of a given job/task.

A progress bar may be horizontal or vertical. It may display an icon besides it, as well as primary and units labels. The former is meant to label the widget as a whole, while the latter, which is formatted with floating point values (and thus accepts a printf-style format string, like "%1.2f units"), is meant to label the widget’s progress value. Label, icon and unit strings/objects are optional for progress bars.

A progress bar may be inverted, in which case it gets its values inverted, i.e., high values being on the left or top and low values on the right or bottom, for horizontal and vertical modes respectively.

The span of the progress, as set by span_size, is its length (horizontally or vertically), unless one puts size hints on the widget to expand on desired directions, by any container. That length will be scaled by the object or applications scaling factor. Applications can query the progress bar for its value with value.

## Flip

This widget holds two content efl.evas.Object: one on the front and one on the back. It allows you to flip from front to back and vice-versa using various animations.

If either the front or back contents are not set the flip will treat that as transparent. So if you were to set the front content but not the back, and then call Flip.go() you would see whatever is below the flip.

For a list of supported animations see Flip.go().

## Check

The check widget allows for toggling a value between true and false.

Check objects are a lot like radio objects in layout and functionality, except they do not work as a group, but independently, and only toggle the value of a boolean state between false and true.

## Label

Widget to display text, with simple html-like markup.

The Label widget doesn’t allow text to overflow its boundaries, if the text doesn’t fit the geometry of the label it will be ellipsized or be cut.

## Icon

An icon object is used to display standard icon images (“delete”, “edit”, “arrows”, etc.) or images coming from a custom file (PNG, JPG, EDJE, etc.), on icon contexts.

The icon image requested can be in the Elementary theme in use, or in the freedesktop.org theme paths. It’s possible to set the order of preference from where an image will be fetched.

This widget inherits from the Image one, so that all the functions acting on it also work for icon objects.

You should be using an icon, instead of an image, whenever one of the following apply:

you need a thumbnail version of an original image
you need freedesktop.org provided icon images
you need theme provided icon images (Edje groups)
Default images provided by Elementary’s default theme are described below.

These are names that follow (more or less) the Freedesktop icon naming specification. Use of these names are preferred, at least if you want to give your user the ability to use other themes. All these icons can be seen in the elementary_test application, the test is called “Icon Standard”.

## Frame

Frame is a widget that holds some content and has a title.

## queue.Queue

```
class Queue(builtins.object)
 |  Queue(maxsize=0)
 |  
 |  Create a queue object with a given maximum size.
 |  
 |  If maxsize is <= 0, the queue size is infinite.
 |  
 |  Methods defined here:
 |  
 |  __init__(self, maxsize=0)
 |      Initialize self.  See help(type(self)) for accurate signature.
 |  
 |  empty(self)
 |      Return True if the queue is empty, False otherwise (not reliable!).
 |      
 |      This method is likely to be removed at some point.  Use qsize() == 0
 |      as a direct substitute, but be aware that either approach risks a race
 |      condition where a queue can grow before the result of empty() or
 |      qsize() can be used.
 |      
 |      To create code that needs to wait for all queued tasks to be
 |      completed, the preferred technique is to use the join() method.
 |  
 |  full(self)
 |      Return True if the queue is full, False otherwise (not reliable!).
 |      
 |      This method is likely to be removed at some point.  Use qsize() >= n
 |      as a direct substitute, but be aware that either approach risks a race
 |      condition where a queue can shrink before the result of full() or
 |      qsize() can be used.
 |  
 |  get(self, block=True, timeout=None)
 |      Remove and return an item from the queue.
 |      
 |      If optional args 'block' is true and 'timeout' is None (the default),
 |      block if necessary until an item is available. If 'timeout' is
 |      a non-negative number, it blocks at most 'timeout' seconds and raises
 |      the Empty exception if no item was available within that time.
 |      Otherwise ('block' is false), return an item if one is immediately
 |      available, else raise the Empty exception ('timeout' is ignored
 |      in that case).
 |  
 |  get_nowait(self)
 |      Remove and return an item from the queue without blocking.
 |      
 |      Only get an item if one is immediately available. Otherwise
 |      raise the Empty exception.
 |  
 |  join(self)
 |      Blocks until all items in the Queue have been gotten and processed.
 |      
 |      The count of unfinished tasks goes up whenever an item is added to the
 |      queue. The count goes down whenever a consumer thread calls task_done()
 |      to indicate the item was retrieved and all work on it is complete.
 |      
 |      When the count of unfinished tasks drops to zero, join() unblocks.
 |
 |  put(self, item, block=True, timeout=None)
 |      Put an item into the queue.
 |      
 |      If optional args 'block' is true and 'timeout' is None (the default),
 |      block if necessary until a free slot is available. If 'timeout' is
 |      a non-negative number, it blocks at most 'timeout' seconds and raises
 |      the Full exception if no free slot was available within that time.
 |      Otherwise ('block' is false), put an item on the queue if a free slot
 |      is immediately available, else raise the Full exception ('timeout'
 |      is ignored in that case).
 |  
 |  put_nowait(self, item)
 |      Put an item into the queue without blocking.
 |      
 |      Only enqueue the item if a free slot is immediately available.
 |      Otherwise raise the Full exception.
 |  
 |  qsize(self)
 |      Return the approximate size of the queue (not reliable!).
 |  
 |  task_done(self)
 |      Indicate that a formerly enqueued task is complete.
 |      
 |      Used by Queue consumer threads.  For each get() used to fetch a task,
 |      a subsequent call to task_done() tells the queue that the processing
 |      on the task is complete.
 |      
 |      If a join() is currently blocking, it will resume when all items
 |      have been processed (meaning that a task_done() call was received
 |      for every item that had been put() into the queue).
 |      
 |      Raises a ValueError if called more times than there were items
 |      placed in the queue.
 ```
