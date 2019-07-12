# Kirby Editor

## Installation

### Download

Download and copy this repository to `/site/plugins/{{ plugin-name }}`.

### Git submodule

```
git submodule add https://github.com/{{ your-name }}/{{ plugin-name }}.git site/plugins/{{ plugin-name }}
```

### Composer

```
composer require {{ your-name }}/{{ plugin-name }}
```

## Setup

Once the plugin is installed, you can use the new `editor` field type in your blueprints: 

```yaml
fields: 
  text: 
    label: Editor
    type: editor
```

## In your templates

The editor stores its content in a YAML format. To convert it to HTML you can use the new `blocks` method in your templates. 

```
<?= $page->text()->blocks() ?>
```

## Customizing blocks

You can customize the result of the blocks field method by overwriting individual block snippets. 

Create a new `blocks` folder in `site/snippets`. Each block type can have its own snippet inside the folder. The following block types are currently available. 

- code
- blockquote
- h1
- h2
- h3
- hr
- image
- ol
- paragraph
- ul
- video

Inside a block snippet you get the following variables: 

- `$block`
- `$content`
- `$attrs`

Here's an example how the image block is built: 

```php
<figure>
  <img src="<?= $attrs->src() ?>" alt="<?= $attrs->alt() ?>">
  <?php if ($attrs->caption()->isNotEmpty()): ?>
  <figcaption>
    <?= $attrs->caption() ?>
  </figcaption>
  <?php endif ?>
</figure>
```

Check out the other default block snippets in the snippets folder of the editor plugin, to get a better overview of how the blocks are made. 

## License

MIT

## Credits

- [Bastian Allgeier](https://getkirby.com)
