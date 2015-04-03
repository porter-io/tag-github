# Tag Github

> A community effort to tag Github repos.

There are millions of repos on Github and many active Github users starred hundreds of them.
As the usage grows, organizing and discovering repos became more and more important.
[Some users](https://github.com/kessler/add-tags-to-github-stars) requested Github to add tagging feature and
[others](https://github.com/bayandin/awesome-awesomeness) started to build curated lists about topics they care.

By working together, let's build a shared dataset about repo tags which could benefit everyone in the open source community.

## Demo

We've put up a [DEMO] in which you can see some rankings and do some filtering on the data.

## Contributing

Contributing is simple. Just fork this repo, tag your repos with the [Tagg Utility/Library], then send us a Pull Request with changes you made.
You can also [create an issue](https://github.com/porter-io/tag-github/issues/new) if you have any suggestions or ideas.

Please read the [Contributing Guide] for more details.

## Usage

**Explore The Dataset**

The data structure is dead simple and easy to work with. You can play with the data using any utility that works with directories and symlinks.

For example, we can check what tags a repo has just using `ls`

```bash
> ls repos/angular/angular.js
angular  framework  frontend-framework  google
javascript  __meta__.json  official  original
```

Or using the **tagg** cli for a nicer output

```bash
> tagg repos show angular/angular.js
Github Repos - angular/angular.js
Exists: True Loaded: True
{
  "created_at": "2015-02-27T22:28:20.155553",
  "description": "HTML enhanced for web apps",
  "fork": false,
  "full_name": "angular/angular.js",
  "language": "JavaScript",
  "updated_at": "2015-03-21T14:55:07.593941"
}

Links:
Tags - general/angular
Tags - general/framework
Tags - general/frontend-framework
Tags - brand/google
Tags - language/javascript
Tags - general/official
Tags - general/original

```

We can get also all web frameworks using find

```bash
> find repos -name web-framework
repos/strongloop/express/web-framework
repos/dropwizard/dropwizard/web-framework
repos/slimphp/slim/web-framework
repos/meteor/meteor/web-framework
repos/servicestack/servicestack/web-framework
repos/astaxie/beego/web-framework
repos/yiisoft/yii2/web-framework
repos/yiisoft/yii/web-framework
...
```

Or using the **tagg** cli to do some cross-filtering

```bash
> tagg repos links web-framework,python
django/django-old
django/django
tornadoweb/tornado
webpy/webpy
bottlepy/bottle
mitsuhiko/flask
```

**Use the data in your project**

```bash
> tagg export > output.json
```

Or directly use **tagg** to manipulate the data

```python
#! /usr/bin/env python
import tagg

tagstore = tagg.UniqueCachedMetaStore('Tag Store', './tags')
repostore = tagg.GithubMetaStore('Github Meta Store', './repos', [tagstore])

tag_python = tagstore.get('python')
tag_framework = tagstore.get('framework')

print repostore.find_links([tag_python, tag_framework])
```

# FAQ

**1. How large is this dataset?**

For performance reasons, we've only added repos mentioned by at least one HackerNews story.
Currently there are 37190 tagged repos and 518 tags. More repos and tags will be added in the future.

**2. Why plain text?**

We decided to store all data in plain text to make Pull Request easier to use.

**3. Who are you?**

We are developers from [Porter.io](https://porter.io) which is a free service to send daily digest of HackerNews stories about
your favorite Github repos.

# Learn More

[Design Document](DESIGN.md)

[Tagg Utility/Library]

[Contributing Guide]

# License

CC BY-SA 4.0

[DEMO]: https://porter.io/explore/tags/
[Tagg Utility/Library]: https://github.com/porter-io/tagg-python
[Contributing Guide]: CONTRIBUTING.md
