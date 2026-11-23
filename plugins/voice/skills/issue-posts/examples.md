# Examples

Issue summaries Pieter posted on drupal.org between February 2025 and May
2026, and comments posted between February 2025 and August 2026, word for
word. Issue references are shown the way drupal.org renders them.

## Issue summary

> ### Problem/Motivation
>
> One of the goals for the 3.0 roadmap is to set the minimum PHP version to
> 8.3 so we can adopt new PHP practices which cannot be done in 2.x because
> they would break backwards compatibility.
>
> We will be able to use major new features like readonly classes, trait
> constants, typed constants etc.
>
> We should do this before issuing the first 3.0.0 alpha release.

> ### Problem/Motivation
>
> Getting a deprecation warning on PHP 8.3 when running tests:
>
> > Deprecated: strpos(): Passing null to parameter #1 ($haystack) of type
> > string is deprecated in
> > /modules/contrib/tmgmt/translators/tmgmt_local/src/Menu/TMGMTLocalBreadcrumbBuilder.php
> > on line 23
>
> The code in question is this:
>
> ```php
>     if (strpos($route_match->getRouteName(), 'view.tmgmt_local_manage_translate_task') === 0 || strpos($route_match->getRouteName(), 'view.tmgmt_local_task_overview') === 0 ||
>       $route_match->getParameter('tmgmt_local_task') instanceof LocalTaskInterface || $route_match->getParameter('tmgmt_local_task_item') instanceof LocalTaskItemInterface) {
>       return TRUE;
>     }
> ```
>
> It happens because `$route_match->getRouteName()` can return `NULL` if there
> is no route, e.g. when running on the CLI.

> ### Problem/Motivation
>
> When Drupal is hosted on multiple instances, the CSV import doesn't work.
> The CSV file is saved in temporary storage of the instance the submit
> handler is processed on, but since temporary storage is not shared across
> multiple web heads, the file is missing on all other instances and cannot be
> processed.
>
> #### Steps to reproduce
>
> 1. Host Drupal on infrastructure that has multiple running instances.
> 2. Import a CSV file containing Texts translations.
>
> Result: the translations are not imported, or at best are partially
> imported.
>
> ### Proposed resolution
>
> Drupal core solves the problem of importing translations in a batch process
> in the Locale module by storing the content of the file in the key-value
> store which allows up to 4GB of serialized data to be stored, ref
> `locale_translation_status_save()`.
>
> We can use the same tactic.

> ### Problem/Motivation
>
> The documentation for `WebformElementInterface::hasMultipleValues()`
> declares that this method returns a boolean, but this is not the full
> picture.
>
> The method can return these values:
>
> 1. `TRUE` if there are unlimited values.
> 2. `FALSE` if only a single value is allowed
> 3. An integer in case a limited number of values are allowed. For example if
>    2 values are allowed it will return `2`
>
> The method is not well named, and there is overlap between this and
> `::supportsMultipleValues()` as well as `::hasMultipleWrapper()`. It is also
> confusing that `FALSE` equates to 1 allowed element. However changing method
> names and/or return values would be a B/C break.
>
> ### Proposed resolution
>
> The simplest solution would be to update the documentation to match the
> reality.

## Acknowledgement

> This is looking great, thanks very much!

> Thanks for the feedback @dulnan! I will implement this.

> Starting on this.

> Yay! Thanks very much!

## Status update

> Updated code to work with latest 11.x. There were conflicts due to #3511357:
> Clean up hook implementations in Node module and #3396062: Deprecate most
> methods on NodeStorage.
>
> None of the remarks have been addressed. Now that #3396062: Deprecate most
> methods on NodeStorage is in it is expected that there will be deprecation
> warnings.

> I did the remaining compatibility fixes, but it looks like this still needs
> more work. Some of the updates to the tests look like they might introduce
> new failures. I ran the tests and had a large number of warnings, errors and
> failures. A number of these probably are already happening in the main
> branch.

> I created a new MR because the previous one is outdated now that #3537948:
> Abstract info-collection RedisController to deal with special environments
> is in.
>
> Thanks to the improvements made in that ticket, the fix is now very trivial.

## Review

> Thanks for working on this!
>
> Instead of adding additional code to the form validate handler, let's
> instead mark the field as required in `Registrant::baseFieldDefinitions()`
> as was proposed in the issue summary.
>
> By doing this we will inform Drupal that the field is required. Drupal will
> then take care of the form validation for us. Also it will do some other
> helpful things like marking the field as required, support entity validation
> etc.
>
> We do not need to make any changes to the form, it will all be handled
> automatically :)

> Just updating the version strings is not sufficient. I did a check and the
> following issues also need to be addressed:
>
> - Class `Drupal\mailgun\Commands\MailgunSanitizeCommands` implements
>   deprecated interface `Drush\Drupal\Commands\sql\SanitizePluginInterface`:
>   use `\Drush\Commands\sql\sanitize\SanitizePluginInterface` instead.
> - MailgunMail.php, line 111: Call to deprecated method `renderPlain()`.
>   Deprecated in drupal:10.3.0 and is removed from drupal:12.0.0. Use
>   `Drupal\Core\Render\RendererInterface::renderInIsolation()` instead.

> I reviewed the last commit from @lussoluca, it looks good, and thanks for
> improving the naming of the variables!
>
> I cannot set this to RTBC since I worked on it, but I think the remarks have
> been addressed.

> Thanks a lot for working on this! I have reviewed the code, it's looking
> great so far. I left some comments on the MR. We also need a test. I can
> take care of that.

## Proposal

> Maybe a better solution would be to remove Drupal 9.5 from the supported
> versions and require PHP 8. Both Drupal 9.5 and PHP 7.4 are unsupported so
> the maintainers' efforts are better spent elsewhere.

> Now that we are planning the next major, would it be a good idea to get
> attribute based plugin definitions in? `[#SchemaExtension()]` rather than
> `@SchemaExtension`.

> In the current code base the most common way to detect whether we are
> running on Windows is `str_starts_with(PHP_OS, 'WIN')`. Let's use this for
> consistency.

The closing paragraphs of a longer design comment, after the code samples that
show the problem:

> In 100% of the cases where the collection name is passed in in the current
> code base, it is derived from the index. So let's standardize this on the
> index.
>
> To avoid any confusion in the future, I propose to deprecate the existing
> `getSchema(string $collection_name)` method and replace it with
> `getSchemaForIndex(IndexInterface $index)`. This clearly shows what to pass
> in.

The opening of a proposal that reports an investigation Claude did, and its
reproduction paragraph:

> I ran into the same error and let Claude investigate it. It found the cause.
> The command fails when another process (e.g. on a cron job) is indexing the
> same index at that moment.

> It can be reproduced with an index that has items left to index. In one
> terminal acquire the lock and hold it:
>
> ```
> drush php:eval '\Drupal::lock()->acquire("search_api:index:INDEX_ID", 60); sleep(180);'
> ```
>
> Then in a second terminal, run `drush search-api:index`. It fails with the
> error from the issue summary and exit code 1. Without the lock it works.

## Position

> I have used this patch with great success in several projects. It is great
> to delete some translations that were added by mistake due to inexperienced
> developers passing dynamic strings to `$this->t()`.
>
> Now, this is really helpful in these cases, but in _normal_ usage this issue
> shouldn't really arise. When using good quality stable modules, and custom
> code that has been peer-reviewed, in theory no "bad" source strings should
> be present. So I think this is solving an edge case and should not be
> included in core. It would be great to have this in a small contrib module
> though.
>
> I am in favor of closing this as "Won't fix" and move it to contrib.

## Correction

> I was too quick in deciding to expose the metadata type directly as children
> of container / composite elements. It is actually better to expose
> `WebformElement` because there can be fields on them that are essential for
> rendering the forms in the frontend.
>
> A good example is the "maxlength" for text fields. This is exposed on
> `WebformElementTextBase` which is an interface for `WebformElement`.
>
> So I reverted #3506038: Expose the element metadata directly in nested
> elements again in this MR.

> Moved patch #11 to a MR.
>
> I was wrong in comment #15, the original code does a loose comparison and it
> works as expected when comparing a string with a `SimpleXMLElement` object.
> But I still decided to keep this modest improvement in the MR ;)

## Scoping

> There are multiple different errors being confused here. Let's focus this
> only on the error mentioned in the issue summary. Comments #2 #6 #8 #10 are
> different error messages and are not in scope of this issue.

> Thanks for the review! I created a followup for the coding standards
> violations since these are out of scope, the violations are in files
> untouched by this MR. #3523877: Fix coding standards violations

> Unassigning, let's first figure out the best way to approach this.
