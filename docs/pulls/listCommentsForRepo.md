# List comments in a repository

**Note:** Multi-line comments on pull requests are currently in public beta and subject to change.

Lists review comments for all pull requests in a repository. By default, review comments are in ascending order by ID.

**Multi-line comment summary**

**Note:** New parameters and response fields are available for developers to preview. During the preview period, these response fields may change without advance notice. Please see the [blog post](https://developer.github.com/changes/2019-10-03-multi-line-comments) for full details.

Use the `comfort-fade` preview header and the `line` parameter to show multi-line comment-supported fields in the response.

If you use the `comfort-fade` preview header, your response will show:

- For multi-line comments, values for `start_line`, `original_start_line`, `start_side`, `line`, `original_line`, and `side`.
- For single-line comments, values for `line`, `original_line`, and `side` and a `null` value for `start_line`, `original_start_line`, and `start_side`.

If you don't use the `comfort-fade` preview header, multi-line and single-line comments will appear the same way in the response with a single `position` attribute. Your response will show:

- For multi-line comments, the last line of the comment range for the `position` attribute.
- For single-line comments, the diff-positioned way of referencing comments for the `position` attribute. For more information, see `position` in the [input parameters](https://developer.github.com/v3/pulls/comments/#parameters-2) table.

The `reactions` key will have the following payload where `url` can be used to construct the API location for [listing and creating](https://developer.github.com/v3/reactions) reactions.

```js
octokit.pulls.listCommentsForRepo({
  owner,
  repo
});
```

## Parameters

<table>
  <thead>
    <tr>
      <th>name</th>
      <th>required</th>
      <th>description</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>owner</td><td>yes</td><td>

owner parameter

</td></tr>
<tr><td>repo</td><td>yes</td><td>

repo parameter

</td></tr>
<tr><td>sort</td><td>no</td><td>

Can be either `created` or `updated` comments.

</td></tr>
<tr><td>direction</td><td>no</td><td>

Can be either `asc` or `desc`. Ignored without `sort` parameter.

</td></tr>
<tr><td>since</td><td>no</td><td>

This is a timestamp in [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format: `YYYY-MM-DDTHH:MM:SSZ`. Only returns comments `updated` at or after this time.

</td></tr>
<tr><td>per_page</td><td>no</td><td>

Results per page (max 100)

</td></tr>
<tr><td>page</td><td>no</td><td>

Page number of the results to fetch.

</td></tr>
  </tbody>
</table>

See also: [GitHub Developer Guide documentation](endpoint.documentationUrl).
