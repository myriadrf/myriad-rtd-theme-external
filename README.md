# Remote Content Integration with Read the Docs Theme

This README explains how this project integrates remote HTML content and CSS with the Sphinx Read the Docs theme.

## Remote Content Integration in conf.py

The project fetches remote HTML content and CSS to customize the Sphinx documentation pages:

### 1. Remote HTML Content

In `conf.py`, we use the `requests` library to fetch HTML content from remote URLs:

```python
import requests

def fetch_remote_content(url):
    try:
        response = requests.get(url, verify=True)
        if response.status_code == 200:
            return response.text
        else:
            print(f"Failed to fetch {url}, status code: {response.status_code}")
            return ""
    except Exception as e:
        print(f"Error fetching {url}: {e}")
        return ""

# Fetch navbar and footer content
extrabody_content = fetch_remote_content('https://handbook-concept.netlify.app/hosted/_templates/navbar.html')
extrafooter_content = fetch_remote_content('https://handbook-concept.netlify.app/hosted/_templates/footer.html')
```

This content is then passed to the Jinja2 template context:

```python
html_context = {
    'extrabody': extrabody_content,
    'extrafooter': extrafooter_content,
    # Other context variables...
}
```

### 2. Remote CSS

Remote CSS is included in the documentation using:

```python
html_css_files = ['https://handbook-concept.netlify.app/hosted/_static/mr-custom.css']
```

### 3. Template Integration

The remote content is inserted into the HTML pages using a custom template (`_templates/layout.html`) and (`_templates/footer.html`) at build.

```html
{% extends "!layout.html" %}

{% block extrabody %}
    {{ super() }}
    {{ extrabody|safe if extrabody else "" }}
{% endblock %}

{% extends "!footer.html" %}
{% block footer %}
    {{ super() }}
    {{ extrafooter|safe if extrafooter else "" }}
{% endblock %}
```

## NPM Scripts

This project uses several NPM scripts to automate common tasks:

| Script | Description |
|--------|-------------|
| `npm run start` | Sets up the Python virtual environment and installs required dependencies |
| `npm run build` | Builds the Sphinx documentation using the `make html` command |
| `npm run watch` | Watches for changes in .rst files and automatically rebuilds documentation |
| `npm run serve` | Starts a browser-sync server to preview documentation on port 8000 |
| `npm run dev` | Builds documentation and runs both watch and serve in parallel |

To run any of these scripts, use:

```bash
npm run <script-name>
```

For example, to start the development environment:
NOTE: ensure you have python3-venv installed before running `npm run start`.

```bash
npm run start
npm run dev
```

## How It Works

1. During build time, `conf.py` fetches the remote content
2. The content is injected into the HTML templates via the Jinja2 context
3. The remote CSS is loaded via standard HTML link tags in the final HTML output
4. The custom template (`layout.html`) merges the remote content with the theme's base template
5. The custom template (`footer.html`) merges the remote content with the theme's footer template

NOTE: any changes to the remote content will require rebuilding the documentation.
