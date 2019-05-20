# Notes

## HTTP

- HTTP (Hypertext Transfer Protocol) is one of many protocols operating in the application layer of the internet
  - Relies on the transport layer
  - Supports the World Wide Web
  - Interactions are between a client/server
    - Client makes requests to a server
  - Resources are located by Uniform Resource Locators (URLs)
  - URLs have 3 parts (e.g `http://www.gnu.org/licenses/licenses.html`):
    - `http` is the scheme name
    - `www.gnu.org` is the host where the resource is to be found
    - `/licenses/licenses.html` is the path, specifying to the host where to find the resource
  - Clients use the URL's host part to establish a connection, and the path to send a request to the server
    - Requests are text strings, e.g: `GET /licenses/licenses.htmlHTTP/1.1`
  - The server responds with a message including a representation of the resource requested
    - Typically, this is a text document containing Hypertext Markup

## HTML

- HTML (Hypertext Markup Language) is a way of representing things that a web browser can present to a user effectively, enabling the user to navigate between related documents
- Web technology is not well defined like TCP or IP, there's a set of specs but which are sometimes broken
  - HTML has tags that describe the document content
    - Not used to describe the exact appearance, but rather the layout
  - Images, hyperlinks and tables all have tags
  - HTML standards are controlled by the World Wide Web Consortium (W3C)
    - However standards evolve and some web browsers aren't fully compliant
  - The Semantic Web is an attempt to go further by allowing web pages to represent relationships between elements that relates to their meaning for humans

### Example Page

- [GNU website](http://www.gnu.org/licenses/licenses.html)
- And the HTML

```html
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN""http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
  <head>
    <!--start of server/head-include-1.html -->
    <meta http-equiv="content-type" content="text/html; charset=utf-8" />
    <link rev="made" href="mailto:webmasters@gnu.org" />
    <title>Licenses-GNU Project -Free Software Foundation</title>
  </head>
  <body>
    <ul>
      <li id="tabAboutGNU"><a href="/gnu/gnu.html">ABOUT&nbsp;GNU</a></li>
      <li id="tabPhilosophy"><a href="/philosophy/philosophy.html">PHILOSOPHY</a></li>
    </ul>
    Header —meta-informationBody —main contentSemanticmarkupHTML entity 6of 9
    <h2>Licenses</h2>
    <div id="mission-statement">
      <p>
        The <a href="http://www.fsf.org">Free Software Foundation</a>is the principal organizational sponsor of the GNU Operating System.
        <strong>Support GNU and the FSF</strong>by <a href="http://shop.fsf.org/">buying manuals and gear</a>,
      </p>
    </div>
    <!--/mission-statement -->
  </body>
</html>
```

## Web Search

### Topic-based directories

- Web search is one of the most important applications of computers
- In the early years of WWW, topic-based directories were one of the main ways to search for information
  - Yahoo Directory (from 1994 onwards) was one of the most popular:
    ![Yahoo Directory](https://i.imgur.com/OwMdXa7.png)
- Within 5 years, the directories were made obsolete by automated search
- Google dominates since it had better search technology than anyone else in the early 2000s
  - Also had a good strategy to make money out of search

### Search Engines

- There are 5 main processes
  - In the background:
    - Run a program (a crawler) that generates http requests analyses the content to extract URLs and then generates more http requests using them
    - Build an index to the web pages found so that it is possible to find all pages containing a given word
  - At query time:
    - Accept a query from a user via http(s)
    - Lookup the query words in the index and intersect the results sets to a candidate set of web pages
    - Rank the web pages in order of 'citation importance' and return the list to the user
    - Search engines are ignorant of the meaning of the text they are handling:
      - Search is based largely on string matches of words/phrases and hyperlink structure

## Cloud Computing

- Allows computing resources to be shared over the internet, achieving economies of scale (meaning we don't have to make our own web server)
- Storage, processing and resources are supplied as a service across the internet
  - By a provider to end users who access them through a web browser, virtual desktop application, email client, etc.

### Example

- Amazon Web Services, which includes
  - EC2 (Elastic Compute Cloud) - virtual private servers
  - S3 (Simple Storage Service) - remote data storage
  - Cloudfront - distributing data to locations near user
  - Workspaces - device-independent virtual desktops

### Pros/Cons

- Potential advantages
  - More conient management and deployment of applications, since not installed on the user's computer
  - Improved utilization by running server and storage device instances as virtual machines on a single host
  - Rapid scalability and elasticity of resources
  - Increased reliability due to multiple redundant sites
  - Capital (setup/installation) costs converted to operational costs
- Potential disadvantages
  - Greater security risk, since data is stored remotely
  - Reduced control over technical trade-offs
