<!--
{
  "title": "Easy static website builder with HTML, CSS and Typescript or Javascript",
  "time": "2024-12-11T21:00:00.000Z",
  "description": "Fast learning, preprocessing, intuitive website builder Rino.js is your goto web framework for building efficient static websites with HTML, CSS and Typescript/Javascript. Designed for developers of all levels, it simplifies web development by combining the power of standard web technologies with streamlined preprocessing tools. Requirement Node.js HTML CSS Javascript /..."
}
-->

# Fast learning, preprocessing, intuitive website builder

Rino.js is your go-to web framework for building efficient static websites with HTML, CSS and Typescript/Javascript. Designed for developers of all levels, it simplifies web development by combining the power of standard web technologies with streamlined preprocessing tools.

## Requirement
- Node.js
- HTML
- CSS
- Javascript / Typescript

## Quick Start
Getting started is as simple as:
```
npm create rino@latest
```
With just one command, you can set up your project and start developing immediately.

## Why Choose Rino.js for Your Website?
Modern web frameworks like Angular, React, Next.js, Vue, and Nuxt have reshaped web app development, but they often come with challenges such as:

- Higher Costs: Increased expenses for hosting, traffic management, and maintenance.
- Complexity: Steep learning curves, complex rules, and slower build speeds.
- Resource Demands: Higher computing requirements.

Enter Rino.js. Built to simplify the process, Rino.js focuses on standard web technologies: HTML, CSS, and JavaScript. It provides:

- HTML Components: Easily build reusable components.
- Seamless Integration: Use npm packages and libraries for JavaScript. Import CSS files and generate as one.
- Automation Tools: Generate sitemaps, compress images, and more.

Even beginners can grasp the basics of Rino.js within 30 minutes, making it an excellent choice for rapid development. Check out the Project Structure and Syntax guide for a deeper dive.

Rino.js also offers flexibility: it allows you to integrate other frameworks like React or Vue when needed, keeping your project lightweight and manageable.

## Project Structure
Rino.js 2 introduces an intuitive project directory and file structure, emphasizing automation and simplicity.

- `/pages`: Base HTML files for web pages. The file and directory structure directly reflect the final output.
- `/components`: Reusable HTML components. Use them with syntax like:
```
<component @path="/header" @tag="div" />
```
- `/mds`: Markdown files, automatically parsed into HTML.
- `/public`: Static files like images and external assets.
- `/scripts`: JavaScript libraries. Place exportable scripts in /scripts/export/.
- `/styles`: CSS libraries. Exportable styles go in /styles/export/.
- `/contents`: Blogging, content system
- `/content-theme`: content.html and content-list.html for customize content pages.

## Templating with JavaScript/TypeScript
```
<script @type="js">
console.log("<div>Hello, Rino.js!</div>");
</script>
```
## Markdown Support
```
<script @type="md">
# Markdown Title
This is Markdown content inside a HTML file.
</script>
```

## Free, MIT licensed open-source project
Rino.js is an open-source project under the MIT license, free for everyone to use.

## Learn More
- Official Website - https://rinojs.org/
- GitHub Discussions - https://github.com/orgs/rinojs/discussions
- GitHub - https://github.com/rinojs

Start your journey with Rino.js today and redefine how you build a website—faster, simpler, and more intuitively.