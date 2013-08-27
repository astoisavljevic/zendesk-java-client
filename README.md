ZenDesk Java Client
===================

This is a ZenDesk client implementation written in Java using AsyncHttpClient and Jackson.

Using the API
-------------

Start by creating a `ZenDesk` instance

    ZenDesk zd = new ZenDesk.Builder("https://{{your domain}}.zendesk.com")
            .setUsername("...")
            .setToken("...") // or .setPassword("...")
            .build();

If you are behind a proxy, or want to otherwise control the lifecycle of the `AsyncHttpClient` instance
you should pass that through to the builder too. If you don't pass an `AsyncHttpClient` instance to the builder
it will create its own which will be closed by the `ZenDesk.close()` method.

Where methods return paged data sets, an `Iterable` is returned that will lazy-fetch one page at a time until
all records have been fetched, so e.g.

    for (Ticket ticket: zd.getTickets()) {
        ...
    }

will iterate through *all* tickets. Most likely you will want to implement your own cut-off process to stop iterating
when you have got enough data.

Status
------

Here is the status of the various API components:

* [Tickets](http://developer.zendesk.com/documentation/rest_api/tickets.html) ✓
* [Ticket Audits](http://developer.zendesk.com/documentation/rest_api/ticket_audits.html) ✓
* [Incremental Tickets](http://developer.zendesk.com/documentation/rest_api/ticket_export.html)
* [Ticket Fields](http://developer.zendesk.com/documentation/rest_api/ticket_fields.html) ✓
* [Ticket Import](http://developer.zendesk.com/documentation/rest_api/ticket_import.html)
* [Ticket Metrics](http://developer.zendesk.com/documentation/rest_api/ticket_metrics.html)
* [Views](http://developer.zendesk.com/documentation/rest_api/views.html)
* [Users](http://developer.zendesk.com/documentation/rest_api/users.html) ✓
* [Requests](http://developer.zendesk.com/documentation/rest_api/requests.html) ✓
* [User Identities](http://developer.zendesk.com/documentation/rest_api/user_identities.html) ✓
* [Groups](http://developer.zendesk.com/documentation/rest_api/groups.html) ✓
* [Group Membership](http://developer.zendesk.com/documentation/rest_api/group_memberships.html)
* [Custom Agent Roles](http://developer.zendesk.com/documentation/rest_api/custom_roles.html)
* [Organizations](http://developer.zendesk.com/documentation/rest_api/organizations.html) ✓ *except for related info*
* [Search](http://developer.zendesk.com/documentation/rest_api/search.html)
* [Tags](http://developer.zendesk.com/documentation/rest_api/tags.html)
* [Forums](http://developer.zendesk.com/documentation/rest_api/forums.html)
* [Forum Subscriptions](http://developer.zendesk.com/documentation/rest_api/forum_subscriptions.html)
* [Categories](http://developer.zendesk.com/documentation/rest_api/categories.html)
* [Topics](http://developer.zendesk.com/documentation/rest_api/topics.html)
* [Topic Comments](http://developer.zendesk.com/documentation/rest_api/topic_comments.html)
* [Topic Subscriptions](http://developer.zendesk.com/documentation/rest_api/topic_subscriptions.html)
* [Topic Votes](http://developer.zendesk.com/documentation/rest_api/topic_votes.html)
* [Account Settings](http://developer.zendesk.com/documentation/rest_api/account_settings.html)
* [Activity Stream](http://developer.zendesk.com/documentation/rest_api/activity_stream.html)
* [Attachments](http://developer.zendesk.com/documentation/rest_api/attachments.html) ✓
* [Autocompletion](http://developer.zendesk.com/documentation/rest_api/autocomplete.html)
* [Automations](http://developer.zendesk.com/documentation/rest_api/automations.html)
* [Job Statuses](http://developer.zendesk.com/documentation/rest_api/job_statuses.html)
* [Locales](http://developer.zendesk.com/documentation/rest_api/locales.html)
* [Macros](http://developer.zendesk.com/documentation/rest_api/macros.html)
* [Restrictions and Responsibilities](http://developer.zendesk.com/documentation/rest_api/restrictions.html)
* [Satisfaction Ratings](http://developer.zendesk.com/documentation/rest_api/satisfaction_ratings.html) ✓
* [Sharing Agreements](http://developer.zendesk.com/documentation/rest_api/sharing_agreements.html)
* [Suspended Tickets](http://developer.zendesk.com/documentation/rest_api/suspended_tickets.html)
* [Triggers](http://developer.zendesk.com/documentation/rest_api/triggers.html)

Other notes
-----------
