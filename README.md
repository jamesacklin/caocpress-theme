# City as Our Campus

![CAOC Screenshot](http://dev2.cityasourcampus.org/wp-content/themes/caocpress/screenshot.png)

A Custom WordPress Theme

Author: James Acklin, [Acklin Design](http://www.acklindesign.com)

## About City as Our Campus

City as Our Campus is a resource for the [Winchester Thurston School](http://www.winchesterthurston.org) in Pittsburgh, PA to extend and deepen students’ learning by utilizing and partnering with community co-educators. To learn more about the program, visit [the CAOC website](http://www.cityasourcampus.org/about).

## Requirements

The theme requires the [Advanced Custom Fields plugin](http://www.advancedcustomfields.com/), as well as the [ACF Repeater add-on](http://www.advancedcustomfields.com/add-ons/repeater-field/) and the [Tag Pages](https://wordpress.org/plugins/tag-pages/) plugin.

## Installation

1. In your admin panel, go to Appearance -> Themes and click the Add New button.
2. Click Upload and Choose File, then select the theme's ZIP file. Click Install Now.
3. Click Activate to use the theme right away.

## Frequently Asked Questions

### How do I change the main navigation?

1. In your admin panel, go to Appearance -> Menus.
2. Drag the pages under "Menu Structure" to rearrange them.
3. To add a menu item, click the "View All" tab under "Pages," click the checkbox next to the page you want to add, and click the "Add to Menu" button.
4. To remove a menu item, click the down arrow in the menu item title and click "Remove."
5. To rename a menu item, click the down arrow in the menu item title and type your name into the "Navigation Label" field.
6. Click "Save Menu" when you are done.

### How do I change the footer?

1. In your admin panel, go to Appearance -> Widgets.
2. Drag widgets to the "Global Footer" object to the right.
3. To edit a footer item, click the down arrow in the title of each widget. As of January 2015, there are three Text widgets: one for the Winchester Thurston information, a blank placeholder widget, and the contact information. These all use raw HTML, so edit with care.
4. Click "Save" on the widget edit panel to save.

### How do I change sidebar items on a page or a post?

1. Edit a page or a post.
2. Scroll all the way to the bottom of the edit page, below the main content editor. To add a sidebar item for that page, click the "Add Sidebar Block" button.
3. Fill in the form. Provide some header text for the section, and use the rich-text editor to compose the text, images, or video you want in this area.
4. To remove an item from the sidebar, hover over the gray space immediately to the right of the rich-text editor and click the minus sign ("-") button that appears.
5. Click "Update" in the Publish section at the top of the editor page to save your changes.

### How do I change links to related pages on a page?

1. Edit a page or a post.
2. Scroll below the main content editor on the edit page. Click "Add Link Section."
3. This will create a group of related pages. Name the group something like, "Additional Resources," or "Learn More," or something that tells the user that there are more articles to read on the particular subject matter. You can create multiple page groups to link to pages across multiple subjects (check out the "Toolkit" page for an example).
4. Click "Add Page" under "Pages to Include" to add a link to a related page.
5. Select the page you want to link to in the drop-down that appears.
6. Similar to deleting sidebar items, you can delete groups or pages within a group by hovering over the right margin next to the row and hitting the minus symbol.
7. Click "Update" in the Publish section at the top of the editor page to save your changes.

## Editorial Notes
- Images should be cropped to 16:9.
- Use appropriate heading tags (`<H3 />` through `<H6 />`) in article copy, rather than styled paragraphs.
- The homepage video is stored in the theme directory and is hard-coded into the page. It is not managed with the WordPress Media Library. If or when it comes time to change the video, contact your friendly Web development freelancer.
- Pages have their own tags, and Posts have *their* own tags. Both show up in the tag archive page.
- Try to maintain page heirarchy using parent and child relationships between pages. For example, when adding a Portfolio item, set the pages' parent to "Portfolio." When adding a page to the About section, set that page's parent to "About." The [CMS Tree View](https://wordpress.org/plugins/cms-tree-page-view/) plugin helps with visualizing and sorting pages in a heirarchy.

## Administrative Notes

### Backing up the WordPress Database
I use [Sequel Pro](http://www.sequelpro.com/) on my Mac for most MySQL operations, which simplifies things greatly with intuitive commands like "Export" and "Import." However, the command line interface for MySQL is pretty easy once you get the hang of it. I assume you'll be doing this on the Windows box, or via RDP.

1. Open the Windows PowerShell application. This command prompt acts similarly to *NIX, so if you're familiar with that filesystem, all your favorite commands will work.
2. Enter the following command: `mysqldump -u [username] -p [database] > backup.sql`
3. Enter the password for the specified user.
4. This will dump the file `backup.sql` into the working directory.
5. Periodically, zip up the `/wp-content/uploads` directory and stash that somewhere, too.
6. Alternately, use the [iThemes Security](https://wordpress.org/plugins/better-wp-security/) plugin to manage database backups.

### Restoring the WordPress Database

1. Fire up the PowerShell and navigate to whatever directory you're storing backup.sql.
2. Run the following command: `mysql -u [username] -p [database] < backup.sql`
3. Enter the password for the specified user.
4. You will over-write all the tables in the specified database with those in the `backup.sql` file.

## Development Notes
- The theme uses [SASS](http://sass-lang.com/) + [Compass](http://compass-style.org/) for styling and [Bower](http://www.bower.io) for dependency management.
- The JavaScript dependencies are included in the compiled `main.min.js` file, but their source files are not included in this repository. They must be installed with Bower (with the help of the `bower.json` file).
- The project is also set up with [CodeKit](https://incident57.com/codekit/) to compile SASS on the fly and concatenate / minify JavaScript.
- The home page content is managed almost entirely with Advanced Custom Fields. Pages and Posts use ACF to handle the "related links" sections and the sidebar contents.
- Be warned: a lot of the page layout uses the [relatively young](http://caniuse.com/#search=flexbox) wonder that is the [Flexible Box](http://www.w3.org/TR/css3-flexbox/). Some preliminary research determined that most of the site's visitors will be using higher-end hardware (Macs or iDevices) with modern browsers (mobile Safari / Firefox / Chrome), so this decision was not made arbitrarily. The benefits of using a modern layout engine greatly outweighed the need to support every browsing environment, everywhere. This might come back to bite us, but who knows. There are SASS mixins to help with this, and Compass is configured (via CodeKit settings) to compile Flexbox back to IE10.