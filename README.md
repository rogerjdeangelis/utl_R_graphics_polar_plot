# utl_R_graphics_polar_plot.sas
R_graphics_polar_plot. Keywords: sas sql join merge big data analytics macros oracle teradata mysql sas communities stackoverflow statistics artificial inteligence AI Python R Java Javascript WPS Matlab SPSS Scala Perl C C# Excel MS Access JSON graphics maps NLP natural language processing machine learning igraph DOSUBL DOW loop stackoverflow SAS community.

    R_graphics_polar_plot

    I am not suggesting you use this like a pie chart.
    I am thinking along the lines of the CERN Large Hadron Collider particle colisions.

    see  graphic
    https://github.com/rogerjdeangelis/utl_R_graphics_polar_plot.sas/blob/master/utl_R_graphics_polar_plot.pdf
    https://tinyurl.com/yajohboa

    github
    https://github.com/rogerjdeangelis/utl_R_graphics_polar_plot.sas

    see
    https://stackoverflow.com/questions/51032312/radial-plot-using-ggplot2

    Divibisan profile
    https://stackoverflow.com/users/8366499/divibisan

    INPUT
    =====

     WORK.HAVE total obs=10

       VARIABLE    VALUE

          1          9
          2          4
          3          2
          4          6
          5          5
          6          3
          7          5
          8          7
          9          6
          10         2


    PROCESS
    =======

    %utl_submit_wps64('
    libname sd1 "d:/sd1";
    options set=R_HOME "C:/Program Files/R/R-3.3.2";
    libname wrk  sas7bdat "%sysfunc(pathname(work))";
    proc r;
    submit;
    source("C:/Program Files/R/R-3.3.2/etc/Rprofile.site", echo=T);
    library(ggplot2);
    se <- function(x) sqrt(var(x)/length(x));
    set.seed(9876);
    pdf(file="d:/pdf/utl_R_graphics_polar_plot.pdf");
    DF <- data.frame(variable = as.factor(1:10),
                     value = sample(10, replace = TRUE));
    ggplot(DF, aes(variable, value, fill = variable)) +
     geom_bar(width = 1, stat = "identity", color = "white") +
     geom_errorbar(aes(ymin = value - se(DF$value),
           ymax = value + se(DF$value),
           color = variable),
           width = .2) +
     scale_y_continuous(breaks = 0:nlevels(DF$variable)) +
     theme_gray() +
     theme(axis.ticks = element_blank(),
           axis.text = element_blank(),
           axis.title = element_blank(),
           axis.line = element_blank()) +
     coord_polar();
    dev.off();
    endsubmit;
    ');


    OUTPUT
    ======

    see
    https://tinyurl.com/yajohboa
    https://github.com/rogerjdeangelis/utl_R_graphics_polar_plot.sas/blob/master/utl_R_graphics_polar_plot.pdf

    *                _               _       _
     _ __ ___   __ _| | _____     __| | __ _| |_ __ _
    | '_ ` _ \ / _` | |/ / _ \   / _` |/ _` | __/ _` |
    | | | | | | (_| |   <  __/  | (_| | (_| | || (_| |
    |_| |_| |_|\__,_|_|\_\___|   \__,_|\__,_|\__\__,_|

    ;

    options validvarname=upcase;
    libname sd1 "d:/sd1";
    data sd1.have;
     input variable value;
    cards4;
     1 9
     2 4
     3 2
     4 6
     5 5
     6 3
     7 5
     8 7
     9 6
     10 2
    ;;;;
    run;quit;

    *          _       _   _
     ___  ___ | |_   _| |_(_) ___  _ __
    / __|/ _ \| | | | | __| |/ _ \| '_ \
    \__ \ (_) | | |_| | |_| | (_) | | | |
    |___/\___/|_|\__,_|\__|_|\___/|_| |_|

    ;

    see process


