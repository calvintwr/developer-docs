<hr>
<section class="full-section">

## Object Hierarchy

> ![Asana object hierarchy](https://luna1.co/b07faf.png)

Asana is a work tracking and collaboration tool. This guide is designed to give developers building on Asana’s API a brief overview of how Asana is structured.  It’s not meant to be exhaustive and may be too basic for experienced Asana users, but read on if you're not a user of Asana who uses it regularly.  The intention is to describe the fundamental elements of Asana to help you scope apps and avoid common points of confusion.   

### How work in Asana is organized

#### Tasks

Tasks are the basic unit of action in Asana.  Tasks have many fields including a single assignee, name, notes, followers (aka collaborators), likes, and comments. Tasks inherit custom fields from their parent project(s). Custom fields values are set for each individual task.  

In addition to standard Create / Read / Update / Delete operations, there are a few things to watch out for when working with tasks:

1. Tasks can be orphaned and belong to no projects, they can belong to one project, or they can be multi-homed across two or more projects. The `memberships` field is a collection of the projects with which the task is associated.    
2. Tasks can be multi-homed as subtasks.  For example, task A can be in project B and the same task A can also be a subtask of task C. 

* [Tasks API documentation](#asana-tasks)
* [Tasks in the Asana Product Guide](https://asana.com/guide/help/tasks/actions)

#### Projects

A project is a collection of tasks that can be viewed as a list, board, timeline, and calendar.  Projects can only exist in a single organization or workplace and only belong to a single team.  Projects can be public in the team or private to project members.  Among the many fields associated with projects, they can have global (shared across the organization) or local (project-specific) custom fields.  A project’s custom fields will be displayed on each task within the project.  

* [Projects API documentation](#asana-projects)
* [Projects in the Asana Product Guide](https://asana.com/guide/help/projects/basics)

#### Portfolios

Portfolios are collections of projects (or other portfolios). Custom fields can be added to portfolios in addition to standard fields that are displayed on every portfolio.  These fields provide a high-level overview of the status of each project within the portfolio. 

* [Portfolios API documentation](#asana-portfolios)
* [Portfolios in the Asana Product Guide](https://asana.com/guide/help/premium/portfolios)

#### Sections

A section is a group of tasks within a project. Sections let you divide tasks into categories, workflow stages, priorities, and more.

* [Sections API documentation](#asana-sections)
* [Sections in the Asana Product Guide](https://asana.com/guide/help/projects/sections)


#### Subtasks

A subtask is exactly the same as tasks in a project except that one (and only one) of its parents is a task (although subtasks can also simultaneously be organized into projects). To check if a task has a subtask, include the `num_subtasks` field when fetching the parent task.   

Things to note when working with subtasks:

1. Subtasks do not inherit the projects of their parent tasks.  
2. There can be up to 5 levels of subtasks below a task. We do not recommend making sub-subtasks. 
3. There is no way to fetch all subtasks of all tasks in a project in a single request. 

* [Subtasks API documentation](#get-subtasks-from-a-task)
* [Subtasks in the Asana Product Guide](https://asana.com/guide/help/tasks/subtasks)

### How users of Asana are organized

#### Workspaces

A workspace is the highest-level organizational unit in Asana. All projects, tasks, and teams have an associated workspace.

* [Workspace / Organization API documentation](#asana-workspaces)
* [Workpsaces in the Asana Product Guide](https://asana.com/guide/help/workspaces/basics)

#### Organizations

An organization is a special kind of workspace that represents a company. Organizations connect all the employees at a company using Asana in a single space based on the company’s shared email domain. In an organization, you can group your projects into teams. 

* [Workspace / Organization API documentation](#asana-workspaces)
* [Organizations in the Asana Product Guide](https://asana.com/guide/help/organizations/basics)

#### Teams

Teams are a subset of users in an organization who collaborate on projects together. Every project in an organization is associated with one team. [Team conversations](https://asana.com/guide/help/conversations/team-conversations) are not currently available in the API.

* [Teams API documentation](#asana-teams)
* [Teams in the Asana Product Guide](https://asana.com/guide/help/organizations/team-basics)

#### Users

A user object represents an account in Asana that can be given access to various workspaces, projects, and tasks.  Asana accounts are free and tied to individuals; Asana accounts grant access to one or more shared Workspaces and Organizations to collaborate with other Asana users.

* [Users API documentation](#asana-users)
* [Users & Guests in the Asana Product Guide](https://asana.com/guide/help/organizations/basics#gl-people)

#### Guest Users

Users can invite clients, contractors, customers, or anyone else who does not have an email address at an approved Organization email domain. These users join as Organization Guests. Guests have limited access in an Organization -- they can only see what’s explicitly shared with them.

Note: it can be advantageous to use guests to create bot accounts. Due to the access restrictions, bots created from a guest account Personal Access Token can be given fine-grained access to only the data that it needs to use.   

* [Users API documentation](#asana-users)
* [Users & Guests in the Asana Product Guide](https://asana.com/guide/help/organizations/basics#gl-people)

</section>
