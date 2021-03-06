# Bioschemas Website
This repo contains the files for the Bioschemas website. The website is deployed on [GitHub](https://github.com/) using [Jekyll](https://jekyllrb.com/).

## Getting Started

If you already have Ruby installed on your machine, then the following files will allow you to get started by installing the relevant dependencies:

- Install Jekyll and Dependencies: ```gem install jekyll bundler jekyll-redirect-from``` and ```gem install jekyll-sitemap```
- Clone the repository: ```git clone https://github.com/Bioschemas/bioschemas.github.io.git```
- Run the website: ```jekyll serve```

If you need more help with installing Jekyll, then see their [installation instructions](https://jekyllrb.com/docs/installation/) for full details.

Note, if you use the GitHub pages documentation, then you will need a `Gemfile` with the following contents ([Gemfile](https://github.com/BioSchemas/bioschemas.github.io/blob/f4b66c8761841994f0b4e02b3d8ffa06b342af78/Gemfile)):

```ruby
source 'https://rubygems.org'
gem 'github-pages', group: :jekyll_plugins
```

## Collections

The website uses a series of [collections](https://jekyllrb.com/docs/collections/) that are configures in the `_config.yml` file. There are collections for:

- Groups: `_groups`
- Meetings: `_meetings`
- People: `_people`
- Profiles: `_profiles`
- Types: `_types`
- Use Cases: `_useCases`

## Site Data

### Live Deployments

The list of live deployments is maintained in the JSON-LD file `_data/live_deployments.json`. The file conforms to the JSON-Schema defined in `_data/live_deployments_schema.json`. Upon pushing to GitHub, an action checks the live deployments data file conforms to the schema file.

A resource listing in the live deployments file consists of the following JSON keys (optional properties denoted with a `?`, `+` indicates one or more required:

- `name`
- `description?`
- `keywords?`: ["CDR", "DDR", "RIR"]
- `url`
- `nodes?`: ELIXIR node two letter code
- `sitemap?`
- `profiles+`:
  - `profileName`: Valid profile name
  - `conformsTo`
  - `exampleURL`
  - `highlight?`

### Profile and Type Status

The status of specification files, i.e. latest draft, release, or deprecated, is controlled by the following data files:

- Profiles: `_data/profile_version.yaml`
- Types: `_data/type_version.yaml`

There should be an entry in each file for each profile/type respectively.

The values of the `latest_publication` and `latest_release` keys should be the corresponding filename (without extension) in the `_profile` or `_type` folder. The `latest_publication` field captures the latest publication (draft or release) of a specification, while the `latest_release` key captures the most recent release. The `latest_release` key may be empty if there has not been a release.

The `status` value is used to distinguish between 'active' specifications, and those that have been 'deprecated'. Deprecated specifications must have a `deprecated_date` value.
