# Acquacotta
R Shiny App to display Run Reports generated by the OICR SeqWare pipeline.
![How it looks](docs/example_look.png)

## Installing
### Requirements
Requires [R 3.3+](https://www.r-project.org/) and the [libv8-dev package](https://packages.ubuntu.com/trusty/libv8-dev)

While in the base directory, execute code in the R console:
```
devtools::install()
```

Before starting Acquacotta, ensure Run Report folders are accessible in the directory specified in the [config file](R/read_config.R). Options that can be modified are:
* Location of Run Report folders
* Default plots to display
* Default metric to sort on

## Running
### R Console
Execute command below:
```
acquacotta::runAcquacotta()
```

### Rscript
Run the command below and open the listed address in a Web Browser:
```bash
Rscript app.R
```

### RStudio
Load the [app.R file](app.R) in RStudio and click the [Run App button or press Command+Shift+Enter](https://shiny.rstudio.com/tutorial/written-tutorial/lesson1/).

### Shiny Server
See the [official documentation](http://docs.rstudio.com/shiny-server/#restarting-an-application) for detailed description on hosting Shiny Apps. To host Acquacotta, make repository visible in the server path (by default /srv/shiny-server and configurable at /etc/shiny-server/shiny-server.conf). 

## Updating
To ensure Shiny Server correctly hosts an updated version of Acquacotta, change the modification time of the [restart.txt file](restart.txt) immediately after an update. On Linux, that can be done by running
```bash
touch restart.txt
```

## Usage
* Use *Select Run Report* drop-down menu to select Run Report to load.
* Use *Select Study* to specify studies to display. By default, all studies are shown for a run.
* Use *Select Lane* to specify which lanes to display. By default, all lanes are shown for a run.
* Specific Libraries can be selected by clicking on the plotted bars. Information on selected Libraries is displayed under the *Selections* tab.
* Use *Order By* to specify on which metric to sort.
* Use *Select Plots* to specify which plots to render.
* Use *Coverage* slider to exclude libraries that lie outside of range.


## Known Issues
* Clicking on Library bars randomly fails to select them
* The UI components cannot be tested, as plotly creates new id variables for each instance: https://github.com/rstudio/shinytest/issues/174
