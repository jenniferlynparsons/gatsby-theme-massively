# Gatsby Theme Massively

Original theme by html5up https://html5up.net/
Converted to Gatsby by https://gatsbytemplates.io/

## Installation

To use this theme in your Gatsby sites, follow these instructions:

1.  Install the theme
    ```sh
    npm i gatsby-theme-massively
    ```

2.  Add the theme to your `gatsby-config.js`:
    ```js
    module.exports = {
      plugins: [
        'gatsby-theme-massively'
      ]
    }
    ```

3. Install dependencies

    ```
    npm i gatsby-plugin-sass node-sass
    ```

4.  Start your site
    ```sh
    gatsby develop
    ```

## Usage

### Pages

In your %pagename%.jsx import Layout component from theme and pass location prop to it:

```
import Layout from 'gatsby-theme-massively/src/components/layout'
import '../styles/main.css'

class About extends React.Component {
  render() {
    console.log(this.props)
    return (
      <Layout location={this.props.location}>
        <Helmet
          htmlAttributes={{ lang: 'en' }}
        />

        <section>
          <header className="main content">
            <h1>About</h1>
          </header>
          <div className="content">We are people</div>
        </section>
      </Layout>
    )
  }
}

```

### Blog Posts

In your src/templates/blog-post.js, make a query and re-export template from theme, following this example:

```
import React from 'react'
import { graphql } from 'gatsby'
import BlogPostTemplate from 'gatsby-theme-massively/src/components/blog-post'

export default BlogPostTemplate

export const pageQuery = graphql`
  query BlogPostBySlug($slug: String!) {
    site {
      siteMetadata {
        title
        author
        description
        social {
          twitter
          facebook
          snapchat
          instagram
          medium
        }
        menuLinks {
          name
          link
        }
        contact {
          info
          email
          tel
          address
        }
      }
    }
    markdownRemark(fields: { slug: { eq: $slug } }) {
      id
      excerpt
      html
      frontmatter {
        title
        date(formatString: "MMMM DD, YYYY")
      }
    }
    allMarkdownRemark(sort: { fields: [frontmatter___date], order: DESC }) {
      edges {
        node {
          excerpt
          fields {
            slug
          }
          frontmatter {
            date(formatString: "DD MMMM, YYYY")
            title
          }
        }
      }
    }
  }
`

```

## Support

Any bugfixes, bug reports and feature requests are welcome.