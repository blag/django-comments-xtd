.. _ref-settings:

========
Settings
========

In order to use Django-comments-xtd it is required to declare the setting `COMMENTS_APP <https://docs.djangoproject.com/en/1.3/ref/contrib/comments/settings/#std:setting-COMMENTS_APP>`_::

    COMMENTS_APP = "django_comments_xtd"

A number of additional settings are available to customize django-comments-xtd behaviour. 


Maximum Thread Level
====================

:index:`COMMENTS_XTD_MAX_THREAD_LEVEL` - Maximum Thread Level

**Optional**

Indicate the maximum thread level for comments. 

An example::

     COMMENTS_XTD_MAX_THREAD_LEVEL = 8

Defaults to 0. What means threads are not permitted.
 

Maximum Thread Level per App.Model
==================================

:index:`COMMENTS_XTD_MAX_THREAD_LEVEL_BY_APP_MODEL` - Maximum Thread Level per app.model basis

**Optional**

A dictionary with `app_label.model` as keys and the maximum thread level for comments posted to instances of those models as values. It allows definition of max comment thread level on a per `app_label.model` basis.

An example::

    COMMENTS_XTD_MAX_THREAD_LEVEL = 0
    COMMENTS_XTD_MAX_THREAD_LEVEL_BY_MODEL = {
        'projects.release': 2,
	'blog.stories': 8, 'blog.quotes': 8, 
	'blog.diarydetail': 0 # not required as it defaults to COMMENTS_XTD_MAX_THREAD_LEVEL
    }


Confirm Comment Post by Email
=============================

:index:`COMMENTS_XTD_CONFIRM_EMAIL` - Confirm Comment Post by Email

**Optional**

This setting establishes whether a comment confirmation should be sent by email. If set to True a confirmation message is sent to the user with a link she has to click on. If the user is already authenticated the confirmation is not sent.

If is set to False the comment is accepted (unless your discard it by returning False when receiving the signal ``comment_will_be_posted``, defined by the Django Comments Framework).

An example::

     COMMENTS_XTD_CONFIRM_EMAIL = True

Defaults to True.


Comment Form Class
==================

:index:`COMMENTS_XTD_FORM_CLASS` - Form class to use when rendering comment forms.

**Optional**

A classpath to the form class that will be used for comments.

An example::

     COMMENTS_XTD_FORM_CLASS = "mycomments.forms.MyCommentForm"


Defaults to `"django_comments_xtd.forms.XtdCommentForm"`.


Comment Model
=============

:index:`COMMENTS_XTD_MODEL` - Model to use

**Optional**

A classpath to the model that will be used for comments.

An example::

     COMMENTS_XTD_MODEL = "mycomments.models.MyCommentModel"


Defaults to `"django_comments_xtd.models.XtdComment"`.


Comment Markup Fallback Filter
==============================

:index:`COMMENTS_XTD_MARKUP_FALLBACK_FILTER` - Default filter to use when rendering comments

**Optional**

Indicate the default markup filter for comments. This value must be a key in the MARKUP_FILTER setting. If not specified or None, comments that do not indicate an intended markup filter are simply returned as plain text.

An example::

    COMMENTS_XTD_MARKUP_FALLBACK_FILTER = 'markdown'

Defaults to None.


Salt
====

:index:`COMMENTS_XTD_SALT` - Extra key to salt the form

**Optional**

This setting establishes the ASCII string extra_key used by ``signed.dumps`` to salt the comment form hash. As ``signed.dumps`` docstring says, just in case you're worried that the NSA might try to brute-force your SHA-1 protected secret.

An example::

     COMMENTS_XTD_SALT = 'G0h5gt073h6gH4p25GS2g5AQ25hTm256yGt134tMP5TgCX$&HKOYRV'

Defaults to an empty string.


Send HTML Email
===============

:index:`COMMENTS_XTD_SEND_HTML_EMAIL` - Enable/Disable HTML email messages

**Optional**

This boolean setting establishes whether email messages have to be sent in HTML
format. By the default messages are sent in both Text and HTML format. By
disabling the setting email messages will be sent only in Text format.

An example::

    COMMENTS_XTD_SEND_HTML_EMAIL = True

Defaults to True.


Threaded Emails
===============

:index:`COMMENTS_XTD_THREADED_EMAILS` - Enable/Disable sending emails in separeate threads

**Optional**

For low traffic websites sending emails in separate threads is a fine solution. However, for medium to high traffic websites such overhead could be reduce by using other solutions, like a Celery application.

An example::

    COMMENTS_XTD_THREADED_EMAILS = True

Defaults to True.
