# Scaling your Apps

## Goal
Demonstrate scaling capabilities of PCF.

## Prerequisites

+ Working PCF Environment
+ CF CLI

## Scaling from the Command Line

1. Open a terminal window and type:

    ```
    $ cf apps
    name                 requested state   instances   memory   disk   urls
    sample-app           started           1/1         1G       1G     
    ```

    Notice the column that shows the current number of instances.  For each of our apps we currently have a single instance deployed.  Let's change that!

1. In your terminal, type:

    `$ cf scale -i 2 sample-app`

1. Type `$ cf apps` in your terminal again and now you will see 2 instances of your application!

    ```
    $ cf apps
    name                 requested state   instances   memory   disk   urls
    sample-app           started           2/2         1G       1G     
    ```