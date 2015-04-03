## Please Contribute by tagging you OWN repos!

> Follow these easy steps and give us a PR.

```bash
# Install tagg utility
> pip install tagg

# Go to data root
> cd tag-github

# This will fetch your github repos and print a list of suggested commands to tag them
> autotagg -g GITHUB_ACCOUNT > pending.txt

# Review and make changes
> vim pending.txt

# Apply changes
> cat pending | tagg

# Validate data
> tagg tags validate
> tagg repos validate
```

## Contribute Guidelines

**Tag a repo**
* Use existing tags.
* Use `autotagg owner/repo` to get suggestions.

**Add a repo**
* `tagg repos add owner/repo` will automatically fetch repo meta information from Github.

**Add a tag**
* Tag names are **unique**. So you can't have **language/python** and **general/python** at the same time.
* Don't add a tag unless it's irreplaceable.
* Add a tag with its full name ex. domain/name
* Open a ticket first unless you are really confident about it.

**Before commit**
* Always run `validate` against tags and repos.
