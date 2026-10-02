Gator

Gator is a command-line RSS feed aggregator written in Go. It allows you to register users, add RSS feeds, follow feeds, and browse posts from the feeds you follow.

Requirements

Before running Gator, make sure you have the following installed:

Go
 — required to build and install the Gator CLI

PostgreSQL
 — required for storing users, feeds, follows, and posts

Git — recommended for working with and contributing to the project

Installation
1. Clone the repository
git clone https://github.com/YOUR-GITHUB-USERNAME/YOUR-REPO-NAME.git
cd YOUR-REPO-NAME

2. Install Gator

Install the Gator CLI using go install:

go install .


This builds and installs the gator binary so that it can be run from your command line without needing go run.

Make sure your Go binary directory is included in your PATH.

You can verify the installation with:

gator

Database Setup

Gator requires a running PostgreSQL database.

Create a PostgreSQL database for the application. For example:

createdb gator


Make sure PostgreSQL is running before starting Gator.

Configuration

Gator uses a configuration file located in your home directory:

~/.gatorconfig.json


Create the file with the following structure:

{
  "db_url": "postgres://username:password@localhost:5432/gator?sslmode=disable",
  "current_user_name": ""
}


Replace the database URL with the connection details for your PostgreSQL installation.

The current_user_name field is updated by Gator when you log in as a user.

Running Gator

Once PostgreSQL is running and your configuration file is set up, you can run Gator:

gator


You can also use:

go run .


during development.

However, for normal use, the installed gator binary should be used instead of go run ..

Commands

Gator provides several commands for managing users, feeds, and posts.

Register a user

Create a new user:

gator register <username>

Log in

Switch the current user:

gator login <username>

List users

View the users registered with Gator:

gator users

Add a feed

Add an RSS feed:

gator addfeed <name> <url>

List feeds

View the RSS feeds known to Gator:

gator feeds

Follow a feed

Follow an existing feed:

gator follow <url>

List followed feeds

View the feeds followed by the current user:

gator following

Aggregate feeds

Fetch posts from the configured RSS feeds:

gator agg <time_between_requests>


For example:

gator agg 10s

Browse posts

View posts from feeds you follow:

gator browse


Depending on the implementation, browse may accept additional arguments such as the number of posts to display.

Development

To run the program directly from the source code during development:

go run .


You can also build the program:

go build


This produces a compiled binary that can be run without the Go toolchain being involved at runtime.

For normal usage, install Gator with:

go install .


and then run:

gator


Go programs are statically compiled binaries, so once Gator has been built or installed, users do not need the Go toolchain to run the resulting binary.

GitHub

The project repository is available at:

https://github.com/YOUR-GITHUB-USERNAME/YOUR-REPO-NAME
