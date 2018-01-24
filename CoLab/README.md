# How to use Colaboratory 

Google’s internal tool to collaborate on AI, write code like documents in google docs and execute it in the cloud. Its perfect especially if you're working with multiple people in real time
coLaboratory Chrome extension  
coLaboratory enables collaboration between people with different skill sets. One example of this would be interactions between programmers who write complex logic in code and non-programmers who are more familiar with GUIs. 

**Step-1** A programmer writes code 

**Step-2** Annotates that code with simple markup to create an interactive form 

**Step-3** The programmer can then hide the complexity of code to show only the form 

This interaction allows programmers to write complex logic in code and allows non-programmers to manipulate that logic through simple GUI hooks.

 
# Quick Start

## Start your project

> Click on File -> Select python version 2/3

## Code Cells

To insert Code Click on **`+ CODE`** in the top toolbar.

``` 
import 'sys'
print('Hello, Colaboratory from Python {}!'.format(sys.version_info[0])) 
```

### How to run cell

- **Click** the **Play** icon in the left gutter of the cell;

- Type `Cmd/Ctrl+Enter` to run the cell in place;

- Type `Shift+Enter` to run the cell and move focus to the next cell (adding one if none exists); or

- Type `Alt+Enter` to run the cell and insert a new code cell immediately below it.

> There are additional options for running some or all cells in the Runtime menu.
 
## How to insert Text 

**Click** on  **`+ TEXT`** in the top toolbar to insert **Text**

- You can double-click to edit this cell. 
- Text cells use markdown syntax. 
 
### How to Markdown Syntax Quick reference
  
- Headers are created using \#. Use multiple \#\#\# for less emphasis. For example:

> \# This is equivalent to an &lt;h1> tag
 
> \##### This is equivalent to an &lt;h5> tag
 
- To make text **bold** surround it with \*\*two asterisks\*\*. 
- To make text *italic* use a \*single asterisk\* or \_underscore\_. \
- _**Bold** inside italics_ and **vice-_versa_** also work.
 
- Blocks are indented with \>, and multiple levels of indentation are indicated by repetition: \>\>\> indents three levels.
- [Links](https://research.google.com/colaboratory) A '!' character in front of a link turns it into an inline image link: !\[Alt text]\(link-to-an-image.png).

**Complete Reference** [Formatting text in Colaboratory: A guide to Colaboratory markdown
](https://colab.research.google.com/notebook#fileId=/v2/external/notebooks/markdown_guide.ipynb&scrollTo=tPqPXAKKkzaM)
 
### [Integration with external dat](https://github.com/PakistanAI/ComputeEasy/blob/master/CoLab/INTEGRATION)

## Move UP and DOWN
You can move a cell by selecting it and clicking **`+CELL UP`** or **`CELL DOWN`** in the top toolbar. 

## System aliases
Jupyter includes shortcuts for common operations, such as ls:
``` 
[] !ls /bin
``` 
 
### How to get backend specs
``` 
[] !df -h
``` 
#### For GPU info, run:
``` 
[] from tensorflow.python.client import device_lib
   device_lib.list_local_devices()
``` 
 
#### For CPU info: 
``` 
 [] !cat /proc/cpuinfo 
 ``` 

#### For RAM: 
``` 
 []!cat /proc/meminfo 
 ``` 
 
## VM spec
- #### Total CPU's

``` 
[] from psutil import *
[] cpu_count()
``` 

- #### Status of CPU
``` 
[] cpu_stats()
``` 
- #### Virtual Memory
``` 
[] virtual_memory()
``` 



## FAQ
#### Where is my code executed? What happens to my execution state if I close the browser window?
Code is executed in a virtual machine dedicated to your account. Virtual machines are recycled when idle for a while, and have a maximum lifetime enforced by the system.

#### How can I get my data out?
You can download any Colaboratory notebook that you’ve created from Google Drive following these instructions

- Go to drive.google.com
- Click a file to download
- (To download multiple files, press Shift or Ctrl while clicking other files.)
- Right-click and click Download
 
- Or from within Colaboratory’s File menu. All Colaboratory notebooks are stored in the open source Jupyter notebook format ( .ipynb).
 
 
:+1:
