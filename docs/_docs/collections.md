---
title: 专题
permalink: /docs/collections/
---

专题是组织相关内容的一个好方法，例如团队的会员资料或者会议的论文等。

## 设置

要使用专题需要先在 `_config.yml` 中设定。例如这里是一个员工专题：

```yaml
collections:
  - staff_members
```

此例中 `collections` 定义一个无附加元数据的序列（例如数组等）。当然，您也
可以为专题 `collections`  定义一些基于映射元数据代替序列，例如：

```yaml
collections:
  staff_members:
    people: true
```

{: .note .info}
定义序列专题时，其页面默认不会被渲染。启用该功能，需要在映射专题中设置
 <code>output: true</code> 。更多详细信息，请查阅<a href="#output">输出</a>。

<div class="note">
  <h5>汇聚您的专题 {%- include docs_version_badge.html version="3.7.0" -%}</h5>

  <p>您可以选择使用 <code>collections_dir: my_collections</code> 来定义存储专题的目录。</p>

  <p>然后 Jekyll 会在 <code>my_collections/_books</code> 寻找 <code>books</code> 专题，在 <code>my_collections/_recipes</code> 寻找 <code>recipes</code> 专题。</p>
</div>

<div class="note warning">
  <h5>请务必将草稿和帖文移动到自定义专题目录中</h5>

  <p>如果您定一个专题目录 <code>collections_dir: my_collections</code> 来存储所有专题，那么就需要将您的 <code>_drafts</code> 和 <code>_posts</code> 目录也移入该专题目录内，如 <code>my_collections/_drafts</code> 和 <code>my_collections/_posts</code>。记住专题目录名字不能以下划线（<code>_</code>）开始。</p>
</div>

## 添加内容

创建相关文件夹（例如 `<source>/_staff_members`）然后添加文档。如果有前置参数，则前置参数被解析，前置参数之后的所有内容被视为 `content` 参数的内容。如果没有前置参数，Jekyll 会将其视为[静态文件]({{'/docs/static-files/' | relative_url }})，内容将不做更多处理。如果有前置参数，Jekyll 会如预期编译内容。

不管前置参数是否存在，只要专题元数据中设置了 `output: true`，Jekyll 就会将所
有文档输出到指定目录（例如 `_site`）。

例如，这就是向上面所述如何添加一个成员会员到专题。
文件名是 `./_staff_members/jane.md`，内容如下：

```markdown
---
name: Jane Doe
position: Developer
---
Jane has worked on Jekyll for the past *five years*.
```

<em>
  切记，尽管在内部被视为一个专题，但是这种设置不适用于[博文](/docs/posts/)。
  文件名有效的博文即使不包含前置参数也会被解析器解析。
</em>

<div class="note info">
  <h5>确保正确命名目录</h5>
  <p>
文件夹名称必须与 <code>_config.yml</code> 文件中定义的一致，并且前面添加 <code>_</code> 符号。
  </p>
</div>

## 输出

Now you can iterate over `site.staff_members` on a page and output the content
for each staff member. Similar to posts, the body of the document is accessed
using the `content` variable:

{% raw %}
```liquid
{% for staff_member in site.staff_members %}
  <h2>{{ staff_member.name }} - {{ staff_member.position }}</h2>
  <p>{{ staff_member.content | markdownify }}</p>
{% endfor %}
```
{% endraw %}

If you'd like Jekyll to create a rendered page for each document in your
collection, you can set the `output` key to `true` in your collection
metadata in `_config.yml`:

```yaml
collections:
  staff_members:
    output: true
```

You can link to the generated page using the `url` attribute:

{% raw %}
```liquid
{% for staff_member in site.staff_members %}
  <h2>
    <a href="{{ staff_member.url }}">
      {{ staff_member.name }} - {{ staff_member.position }}
    </a>
  </h2>
  <p>{{ staff_member.content | markdownify }}</p>
{% endfor %}
```
{% endraw %}

## 永久链接

There are special [permalink variables for collections]({{ '/docs/permalinks/#collections' | relative_url }}) to
help you control the output url for the entire collection.

## 自定义排序文档 {%- include docs_version_badge.html version="4.0" -%}
{: #custom-sorting-of-documents}

By default, two documents in a collection are sorted by their `date` attribute when both of them have the `date` key in their front matter. However, if either or both documents do not have the `date` key in their front matter, they are sorted by their respective paths.

You can control this sorting via the collection's metadata.

### 按前置参数关键词排序

Documents can be sorted based on a front matter key by setting a `sort_by` metadata to the front matter key string. For example,
to sort a collection of tutorials based on key `lesson`, the configuration would be:

```yaml
collections:
  tutorials:
    sort_by: lesson
```

The documents are arranged in the increasing order of the key's value. If a document does not have the front matter key defined
then that document is placed immediately after sorted documents. When multiple documents do not have the front matter key defined,
those documents are sorted by their dates or paths and then placed immediately after the sorted documents.

### 手动排序文档

You can also manually order the documents by setting an `order` metadata with **the filenames listed** in the desired order.
For example, a collection of tutorials would be configured as:

```yaml
collections:
  tutorials:
    order:
      - hello-world.md
      - introduction.md
      - basic-concepts.md
      - advanced-concepts.md
```

Any documents with filenames that do not match the list entry simply gets placed after the rearranged documents. If a document is
nested under subdirectories, include them in entries as well:

```yaml
collections:
  tutorials:
    order:
      - hello-world.md
      - introduction.md
      - concepts/basics.md
      - concepts/advanced.md
```

If both metadata keys have been defined properly, `order` list takes precedence.

## Liquid 属性

### 专题

Collections are also available under `site.collections`, with the metadata
you specified in your `_config.yml` (if present) and the following information:

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
      <th>Variable</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p><code>label</code></p>
      </td>
      <td>
        <p>
          The name of your collection, e.g. <code>my_collection</code>.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>docs</code></p>
      </td>
      <td>
        <p>
          An array of <a href="#documents">documents</a>.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>files</code></p>
      </td>
      <td>
        <p>
          An array of static files in the collection.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>relative_directory</code></p>
      </td>
      <td>
        <p>
          The path to the collection's source directory, relative to the site
          source.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>directory</code></p>
      </td>
      <td>
        <p>
          The full path to the collections's source directory.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>output</code></p>
      </td>
      <td>
        <p>
          Whether the collection's documents will be output as individual
          files.
        </p>
      </td>
    </tr>
  </tbody>
</table>
</div>

<div class="note info">
  <h5>硬编码专题</h5>
  <p>In addition to any collections you create yourself, the
  <code>posts</code> collection is hard-coded into Jekyll. It exists whether
  you have a <code>_posts</code> directory or not. This is something to note
  when iterating through <code>site.collections</code> as you may need to
  filter it out.</p>
  <p>You may wish to use filters to find your collection:
  <code>{% raw %}{{ site.collections | where: "label", "myCollection" | first }}{% endraw %}</code></p>
</div>

<div class="note info">
  <h5>专题和时间</h5>
  <p>Except for documents in hard-coded default collection <code>posts</code>, all documents in collections
    you create, are accessible via Liquid irrespective of their assigned date, if any, and therefore renderable.
  </p>
  <p>Documents are attempted to be written to disk only if the concerned collection
    metadata has <code>output: true</code>. Additionally, future-dated documents are only written if
    <code>site.future</code> <em>is also true</em>.
  </p>
  <p>More fine-grained control over documents being written to disk can be exercised by setting
    <code>published: false</code> (<em><code>true</code> by default</em>) in the document's front matter.
  </p>
</div>

### 文档

In addition to any front matter provided in the document's corresponding
file, each document has the following attributes:

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
      <th>Variable</th>
      <th>Description</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>
        <p><code>content</code></p>
      </td>
      <td>
        <p>
          The (unrendered) content of the document. If no front matter is
          provided, Jekyll will not generate the file in your collection. If
          front matter is used, then this is all the contents of the file
          after the terminating
          `---` of the front matter.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>output</code></p>
      </td>
      <td>
        <p>
          The rendered output of the document, based on the
          <code>content</code>.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>path</code></p>
      </td>
      <td>
        <p>
          The full path to the document's source file.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>relative_path</code></p>
      </td>
      <td>
        <p>
          The path to the document's source file relative to the site source.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>url</code></p>
      </td>
      <td>
        <p>
          The URL of the rendered collection. The file is only written to the destination when the collection to which it belongs has <code>output: true</code> in the site's configuration.
          </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>collection</code></p>
      </td>
      <td>
        <p>
          The name of the document's collection.
        </p>
      </td>
    </tr>
    <tr>
      <td>
        <p><code>date</code></p>
      </td>
      <td>
        <p>
          The date of the document's collection.
        </p>
      </td>
    </tr>
  </tbody>
</table>
</div>
