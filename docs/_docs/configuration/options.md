---
title: 配置项
permalink: "/docs/configuration/options/"
---

下表列出 Jekyll 可用设置和控制其操作的各种<code
class="option">选项（option）</code>（在配置文件中设定）以及<code
class="flag">标志（flag)</code>（在命令行中指定）。

### 全局设置

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
      <th>设置</th>
      <th>
        <span class="option">选项（Option）</span>和<span class="flag">标志（Flag）</span>
      </th>
    </tr>
  </thead>
  <tbody>
    {% for setting in site.data.config_options.global %}
      <tr class="setting">
        <td>
          <p class="name">
            <strong>{{ setting.name }}</strong>
            {% if setting.version-badge %}
              <span class="version-badge" title="Introduced in v{{ setting.version-badge }}">{{ setting.version-badge }}</span>
            {% endif %}
          </p> 
          <p class="description">{{ setting.description }}</p>
        </td> 
        <td class="align-center">
          <p><code class="option">{{ setting.option }}</code></p>
          {% if setting.flag %}
            <p><code class="flag">{{ setting.flag }}</code></p>
          {% endif %}
        </td>
      </tr>
    {% endfor %}
    <tr>
      <td>
        <p class='name'><strong>Defaults</strong></p>
        <p class='description'>
            为<a href="{{ '/docs/front-matter/' | relative_url }}" title="front matter">前置参数</a>设置默认值变量。
        </p>
      </td>
      <td class='align-center'>
        <p>查看<a href="{{ '/docs/configuration/front-matter-defaults/' | relative_url }}" title="details">下表</a></p>
      </td>
    </tr>
  </tbody>
</table>
</div>

<div class="note warning">
  <h5>Destination folders are cleaned on site builds</h5>
  <p>
    The contents of <code>&lt;destination&gt;</code> are automatically
    cleaned, by default, when the site is built. Files or folders that are not
    created by your site will be removed. Some files could be retained
    by specifying them within the <code>&lt;keep_files&gt;</code> configuration directive.
  </p>
  <p>
    Do not use an important location for <code>&lt;destination&gt;</code>; instead, use it as
    a staging area and copy files from there to your web server.
  </p>
</div>

### 编译命令选项

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
      <th>设置</th>
      <th><span class="option">选项（Option）</span>和 <span class="flag">标志（Flag）</span></th>
    </tr>
  </thead>
  <tbody>
    {% for setting in site.data.config_options.build %}
      <tr class="setting">
        <td>
          <p class="name">
            <strong>{{ setting.name }}</strong>
            {% if setting.version-badge %}
              <span class="version-badge" title="Introduced in v{{ setting.version-badge }}">{{ setting.version-badge }}</span>
            {% endif %}
          </p> 
          <p class="description">{{ setting.description }}</p>
        </td> 
        <td class="align-center">
          {% if setting.option %}<p><code class="option">{{ setting.option }}</code></p>{% endif %}
          {% if setting.flag %}<p><code class="flag">{{ setting.flag }}</code></p>{% endif %}
        </td>
      </tr>
    {% endfor %}
  </tbody>
</table>
</div>

### 服务命令选项

In addition to the options below, the `serve` sub-command can accept any of the options
for the `build` sub-command, which are then applied to the site build which occurs right
before your site is served.

<div class="mobile-side-scroller">
<table>
  <thead>
    <tr>
      <th>Setting</th>
      <th><span class="option">Options</span> and <span class="flag">Flags</span></th>
    </tr>
  </thead>
  <tbody>
    {% for setting in site.data.config_options.serve %}
      <tr class="setting">
        <td>
          <p class="name">
            <strong>{{ setting.name }}</strong>
            {% if setting.version-badge %}
              <span class="version-badge" title="Introduced in v{{ setting.version-badge }}">{{ setting.version-badge }}</span>
            {% endif %}
          </p> 
          <p class="description">{{ setting.description }}</p>
        </td> 
        <td class="align-center">
          {% if setting.option %}
            <p><code class="option">{{ setting.option }}</code></p>
          {% elsif setting.options %}
            <p>
              {% for option in setting.options %}
                <code class="option">{{ option }}</code><br>
              {% endfor %}
            </p>
          {% endif %}
          {% if setting.flag %}
            <p><code class="flag">{{ setting.flag }}</code></p>
          {% elsif setting.flags %}
            <p>
            {% for flag in setting.flags %}
              <code class="flag">{{ flag }}</code><br>
            {% endfor %}
            </p>
          {% endif %}
        </td>
      </tr>
    {% endfor %}
  </tbody>
</table>
</div>

<div class="note warning">
  <h5>配置文件中不要使用 Tab 键</h5>
  <p>
    This will either lead to parsing errors, or Jekyll will revert to the
    default settings. Use spaces instead.
  </p>
</div>
