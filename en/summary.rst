Introduction
============

- What is Open Orchesra ? // A brief description of what it is, what you may achieve with it
- Key concepts            // What are a node, a content, a template, an area, a block, a transverse block, a theme, a site, a device, a media, a tag (keyword), a user, a role, a group, a bundle
- The big picture         // Applicative architecture schema, let's talk about Symfony, MongoDB, ESI, etc.

User guide
==========

- First steps             // Connection, main features (site selection, language selection), location of content management, administration
- Site creation           // Basics about hosts, languages, routing
- Template creation       // Creating the page structure with areas
- Node                    // Creating a node from a template, choose your URL pattern, basic configuration
- Node - blocks           // Drag and drop new or existing blocks, configure a block, preview
- Node - versionning      // How to save a node, publish, load a new version
- Content                 // List, create, save, publish a content
- Content - node          // How to use it in a node (blocks : contentList, content)
- Content - type          // Create/edit a new content type
- Blocks                  // Block list reference - quick help for each standard block (start with menu, contentList first)
- Media                   // Manage tree, media and meta-info
- Media - image           // Formats, cropping, upload
- Transverse node/blocks  // About the global page
- Tag                     // Tag management, use of tags in blocks (keywords)
(advanced)
- User                    // User, group management
- Role                    // Role management, grant permissions
- Workflow                // Status, transitions and roles
- API                     // API access keys management
- Routing                 // About routing and redirection management
- Theme                   // Create a theme for your site
- Log                     // User actions log

Developper guide
================

- Install                 // Use of Composer
- Development             // Things to know about package dependency management, npm, grunt, bower, assert-install, etc
- Block                   // Use of command line, things to know about the block FO/BO (strategies, cache control, forms, etc.)
- Create a CRUD           // A CRUD management of any collection
- Add a left panel entry  // Access to a new functionnality
- Device detection        // How to detect device and make alternative block templates
- ESI and Reverse proxy   // Leverage ESI to get high performances
- Twig extensions         // Open Orchestra extensions (theming ?)
- Media                   // Media formats, Gaufrette
- SmartAdmin              // SmartConfirm and others
- Events                  // Open Orchestra events
- Cache                   // Cache/Decache management, cache tags
- Changelog               // Changelog (or link to)

Hosting guide
=============

- Architecture            // System Architecture, web/db servers, reverse proxy, lb, replication, file sharing, etc
- Requirements            // System requirements (Linux kernel, PHP version, etc.)
- Configuration           // Recommended server configurations, crons to install
- Deployment              // Deploy a new version
- Maintenance             // How-to restart services, in which order
- Monitoring              // Which services to monitor
- Backup                  // What to dump, backup
- Logs                    // Where are the system logs, syslog configuration, etc