## Running the example applications

This section explains how to run the OSLC4J Bugzilla Adapter and the NinaCRM example application.



## Installing prerequisites


### Downloading and installing Eclipse

You’ll be using Eclipse and some add-ons to simplify the setup.

You need Eclipse 3.6 or later. [Download Eclipse here](http://eclipse.org/downloads/). Download the **Eclipse IDE for Java EE Developers**.

After you install Eclipse, start the Eclipse application.

In the Workspace Launcher window, create a new directory for your Eclipse workspace or accept the default Workspace location.


### Installing EGit

All of the samples are in Git source control; EGit provides a GUI to work with Git repositories.

1.  In Eclipse, click **Help** &rarr; **Install New Software**.
2.  In the Install window, in the **Work with** field paste in the following: `http://download.eclipse.org/egit/updates`
3.  Click **Add…**.
4.  In the Add Repository window, in the **Name** field, type something memorable like `EGit`, then click **OK**.
5.  Select **Eclipse Git Team Provider** and click **Next**.
6.  On the Install Details page, click **Next**.
7.  On the Review Licenses page, review the license, select **I accept the terms of the license agreement** and click **Finish**.
8.  After EGit installs, on the Software Updates window click __Yes__ to restart Eclipse.


### Installing M2Eclipse

Our samples use the Maven build automation tools; you’ll use the M2Eclipse Maven plugin to manage Maven from Eclipse.

1.  In Eclipse, click **Help** &rarr; **Install New Software**.
2.  In the Install window, in the **Work with** field paste in the following:  
`http://download.eclipse.org/technology/m2e/releases`
3.  Click **Add…**.
4.  In the Add Repository window, in the **Name** field, type something memorable like `M2Eclipse`, then click **OK**.
5.  Select **Maven Integration for Eclipse** and click **Next**.
6.  On the Review Licenses page, review the license, select **I accept the terms of the license agreement** and click **Finish**.
7.  After M2Eclipse installs, on the Software Updates window, click “Yes” to restart Eclipse.

### Installing the OSLC4J toolkit

1.  In Eclipse, open the Git Repositories view. (**Window** &rarr; **Show View** &rarr; **Other**, search for `Git repo` and click **OK**.)
2.  Click **Clone a Git Repository**.
3.  In the Clone Git Repository window, in the **URI** field paste the following:  
`http://git.eclipse.org/gitroot/lyo/org.eclipse.lyo.core.git`  
The **Host** and **Repository** fields will autofill. Leave the **Username** and **Password** fields empty.
4.  Click **Next**.
5.  On the Branch Selection page, select **master** and click **Next**.
6.  For the **Destination**, select a folder for the files or accept the default of your Eclipse workspace.
7.  Click **Finish**. `org.eclipse.lyo.core` will appear in the Git Repositories view.
8.  In the Git Repositories view, right-click **org.eclipse.lyo.core** and click **Import Projects**.
9.  In the Import Projects from Git Repository wizard, select **Import existing projects** and click **Next**.
10.  Select all components of OSLC4J core (this is the default) and click **Finish**.

Next, build the OSLC4J project.

### Build the OSLC4J projects

1.  In Eclipse, open the Project Explorer view. (**Window** &rarr; **Show View** &rarr; **Project Explorer**)
2.  In the Project Explorer view, expand **org.eclipse.lyo.oslc4j.build**.
3.  Right-click on **pom.xml**, then click **Run as** &rarr; **Maven Clean**.
4.  Right-click on **pom.xml**, then click **Run as** &rarr; **Maven Install**. In the Console view, you’ll see a lot fly by; it should end with `BUILD SUCCESS`.

### [Optional] Create an account at Bugzilla Landfill

Landfill is an always-running, open Bugzilla server that you can use if you don’t want to use your own Bugzilla application or set up a new one.

[Create an account here](https://landfill.bugzilla.org/bugzilla-4.2-branch/createaccount.cgi).


## Downloading, building, and running the sample applications


### Cloning the Lyo documentation and server repositories

The Eclipse Lyo documentation Git repository has the Bugzilla Adapter and NinaCRM sample applications.

1.  In Eclipse, open the Git Repositories view. (**Window** &rarr; **Show View** &rarr; **Other**, search for `Git repo` and click **OK**.)
2.  Click **Clone a Git Repository**.
3.  In the Clone Git Repository window, in the **URI** field paste the following:  
`git://git.eclipse.org/gitroot/lyo/org.eclipse.lyo.docs.git`
The **Host** and **Repository** fields will autofill. Leave the **Username** and **Password** fields empty.
4.  Click **Next**.
5.  On the Branch Selection page, select **master** and click **Next**.
6.  For the **Destination**, select a folder for the files or accept the default of your Eclipse workspace.
7.  Click **Finish**. `org.eclipse.lyo.docs` will appear in the Git Repositories view.
8.  Repeat steps 2–7 for the server repository at `git://git.eclipse.org/gitroot/lyo/org.eclipse.lyo.server.git`.

Next, import the documentation projects:

1.  In the Git Repositories view, right-click **org.eclipse.lyo.docs** and click **Import Projects**.
2.  In the Import Projects from Git Repository wizard, select **Import existing projects** and click **Next**.
3.  Select **org.eclipse.lyo.oslc4j.bugzilla** and **ninacrm** and click **Finish**.

Finally, import the server projects:

1.  In the Git Repositories view, right-click **org.eclipse.lyo.server** and click **Import Projects**.
2.  In the Import Projects from Git Repository wizard, select **Import existing projects** and click **Next**.
3.  Select the following projects:
	*   **org.eclipse.lyo.server.oauth.consumerstore**
	*   **org.eclipse.lyo.server.oauth.core**
	*   **org.eclipse.lyo.server.oauth.webapp**
   
	and click **Finish**.


### Configuring the Bugzilla adapter

Configure the Bugzilla adapter to point to your Bugzilla application.

1.  In Eclipse, open the Project Explorer view. (**Window** &rarr; **Show View** &rarr; **Project Explorer**)
2.  In the Project Explorer view, find and edit the file `org.eclipse.lyo.oslc4j.bugzilla/src/main/resources/bugz.properties`.
3.  Edit the `bugzilla_uri` property to the URL of your Bugzilla server. If you’re using Bugzilla Landfill, it will look similar to this:

     `bugzilla_uri=https://landfill.bugzilla.org/bugzilla-4.2-branch`

     There are multiple versions of Bugzilla running at landfill.bugzilla.org; be sure to select the version where you have a user ID.
4.  For the `admin` property, provide your Bugzilla user ID. For Bugzilla Landfill, it will be the email address you used when you created your account:

     `admin=you@example.com`

     (This is the ID you will use to log in to the OAuth application).
5.  Save `bugz.properties`.


### Building the applications

First, update the project configurations for the projects.

1.  In Eclipse, open the Package Explorer view. (**Window** &rarr; **Show View** &rarr; **Package Explorer**)
2.  In the Package Explorer view, select the following packages:

    *   **ninacrm**
    *   **org.eclipse.lyo.oslc4j.bugzilla**
    *   **org.eclipse.lyo.server.oauth.consumerstore**
    *   **org.eclipse.lyo.server.oauth.core**
    *   **org.eclipse.lyo.server.oauth.webapp**

3.  Right-click and select **Maven** &rarr; **Update Project**.
4.  In the Update Maven Project window, verify that those 5 projects are selected and click **OK**.

Next, install the projects:

1. In the Package Explorer view, expand **org.eclipse.lyo.server.oauth.core**.
2. Find the file **pom.xml**
3. Right-click on **pom.xml** and select **Run as** &rarr; **Maven Clean**.
4. Right-click on **pom.xml** and select **Run as** &rarr; **Maven Install**. You should eventually see a success message in the Console view.
5. Repeat steps 1–3 for the following packages _in this order_:

    1.  **org.eclipse.lyo.server.oauth.consumerstore**
    2.  **org.eclipse.lyo.server.oauth.webapp**
    3.  **org.eclipse.lyo.oslc4j.bugzilla**
    4.  **ninacrm**


### Running the sample applications


#### Starting the OSLC4J Bugzilla adapter:

1.  In Eclipse, click **Run** &rarr; **Run Configurations**.
2.  In the Run Configurations window, expand **Maven Build**.
3.  Click **OSLC4JBugzilla**.
4.  Click **Run**. This will start the application.

You will see a lot of messages in the Console view. The application will be running when you see this:

    [INFO] Started Jetty Server
    [INFO] Starting scanner at interval of 5 seconds.

In your web browser navigate to the OSLC Catalog at [http://localhost:8080/OSLC4JBugzilla/services/catalog/singleton](http://localhost:8080/OSLC4JBugzilla/services/catalog/singleton)

Log in with your Bugzilla user ID and password.

#### Starting NinaCRM

1.  In Eclipse, click **Run** &rarr; **Run Configurations**.
2.  In the Run Configurations window, expand **Maven Build**.
3.  Click **Launch NinaCRM**.
4.  Click **Run**. This will start the application.

When the server starts, in your web browser navigate to [http://localhost:8181/ninacrm](http://localhost:8181/ninacrm) to see the NinaCRM example.