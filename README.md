# File Integrity Monitoring

This repo contains documentation for File Integrity Monitoring for VMware Tanzu.

In this README: 

- [File Integrity Monitoring](#file-integrity-monitoring)
  - [Branches in this Content Repo](#branches-in-this-content-repo)
  - [Releasing a new minor version](#releasing-a-new-minor-version)
  - [Partials](#partials)
  - [Contributing to documentation](#contributing-to-documentation)
  - [Publishing docs](#publishing-docs)
    - [Prepare Markdown files](#prepare-markdown-files)
    - [In Docsdash](#in-docsdash)
    - [Promoting to pre-prod and prod](#promoting-to-pre-prod-and-prod)
  - [Troubleshooting Markdown](#troubleshooting-markdown)
  - [Style guide](#style-guide)


## Branches in this Content Repo

As of December 2023:

| Branch name… | Documents version… | Publishes to…                          |
|---------     |--------------------|----------------------------------------|
| main | next unreleased version | https://docs-staging.vmware.com/en/draft/File-Integrity-Monitoring-for-VMware-Tanzu/2.2/fim/GUID-index.html |
| 2.1  | v2.1.x          | Staging at https://docs-staging.vmware.com/en/File-Integrity-Monitoring-for-VMware-Tanzu/2.1/fim/GUID-index.html and production at https://docs.vmware.com/en/File-Integrity-Monitoring-for-VMware-Tanzu/2.1/fim/GUID-index.html |
| 2.0  | Archived as PDF | https://docs.vmware.com/en/File-Integrity-Monitoring-for-VMware-Tanzu/2.0/fim-for-vmware-tanzu-2-0.pdf |
| 1.4  | Archived as PDF | https://docs.vmware.com/en/File-Integrity-Monitoring-for-VMware-Tanzu/1.4/fim-for-vmware-tanzu-1-4.pdf |
| v1.3 | Archived as PDF | https://docs.vmware.com/en/File-Integrity-Monitoring-for-VMware-Tanzu/1.3/fim-for-vmware-tanzu-1-3.pdf |
| v1.2 | Archived as PDF | https://docs.vmware.com/en/File-Integrity-Monitoring-for-VMware-Tanzu/1.2/fim-for-vmware-tanzu-1-2.pdf |

The live branches publish using the docs-book-addon-fim repo and are in these pipelines:

+ https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-services?groups=fim.
+ https://concourse.run.pivotal.io/teams/cf-docs/pipelines/cf-services-edge?groups=fim-edge


## Releasing a new minor version

Because **main** is the latest documentation, the process is to cut an **x.x** branch
for the version that **main** was targeting during that time.

After that, **main** becomes the target for the next minor version of this product.


## Partials

Cross-product partials (if any) for these docs are single sourced from the [Docs Partials](https://github.com/pivotal-cf/docs-partials) repository.


## Contributing to documentation

If there is documentation to add for an unreleased patch version, then create a branch off of the **live** branch
you intend to modify and create a pull request against that branch.
After the version that change is targeting is released, the pull request can be merged and will be live
the next time a documentation deployment occurs.

If the documentation is meant to be target several released versions,
then you will need to:
+ create a pull request for each individual minor version
+ or ask the technical writer to cherry-pick to particular branches/versions.

For instructions on how to create a pull request on a branch and instructions on how to create a
pull request using a fork, see
[Creating a PR](https://docs-wiki.sc2-04-pcf1-apps.oc.vmware.com/wiki/external/create-pr.html)
in the documentation team wiki.


## Publishing docs

- [docworks](https://docworks.vmware.com/) is the main tool for managing docs used by writers.
- [docsdash](https://docsdash.vmware.com/) is a deployment UI which manages the promotion from
staging to pre-prod to production. The process below describes how to upload our docs to staging,
replacing the publication with the same version.

### Prepare Markdown files
- Markdown files live in this repo.
- Images should live in an `images` directory at the same level and linked with a relative link.
- Each page requires an entry in [config/toc.md](config/toc.md) for the table of contents.
- Variables live in [config/template_variables.yml](config/template_variables.yml).

### In Docsdash

1. Wait about 1 minute for processing to complete after uploading.
2. Go to https://docsdash.vmware.com/deployment-stage

   There should be an entry with a blue link which says `Documentation` and points to staging.

### Promoting to pre-prod and prod

**Prerequisite** Needs additional privileges - reach out to a manager on the docs team [#tanzu-docs](https://vmware.slack.com/archives/C055V2M0H) or ask a writer to do this step for you.

1. Go to Staging publications in docsdash  
  https://docsdash.vmware.com/deployment-stage

2. Select a publication (make sure it's the latest version)

3. Click "Deploy selected to Pre-Prod" and wait for the pop to turn green (refresh if necessary after about 10s)

4. Go to Pre-Prod list  
  https://docsdash.vmware.com/deployment-pre-prod

5. Select a publication

6. Click "Sign off for Release"

7. Wait for your username to show up in the "Signed off by" column

8. Select the publication again

9. Click "Deploy selected to Prod"

## Troubleshooting Markdown

| Problem | List displays as a paragraph |
|---------|-----------|
| Symptom:| Bulleted or numbered lists look fine on GitHub but display as a single paragraph in HTML.|
| Solution: | Add a blank line after the stem sentence and before the first item in the list.|

| Problem | List numbering is broken: every item is `1.` |
|---------|-----------|
| Symptom:| Each numbered item in a list is a `1.` instead of `1.`, `2.`, `3.`, etc|
| Solution: | Try removing any blank newlines within each step.|

| Problem | Code boxes not showing |
|---------|-----------|
| Symptom:| VMware publishing system doesn't accept code tags after the three back ticks.|
| Solution: | Make sure you're not using `shell` or `bash` or `console` or `yaml` after back ticks.|


## Style guide

Full name of the add-on for first use on the page: File Integrity Monitoring for VMware Tanzu (FIM)

Subsequent use on the page: "File Integrity Monitoring" or "FIM"

_security metadata_ instead of the other phrases: _security information_ and _security attributes_.
