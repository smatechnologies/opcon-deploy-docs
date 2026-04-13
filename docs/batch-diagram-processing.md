---
title: Batch diagram processing
description: "Reference for the Diagram.SMAOpConDeployClient.exe command-line interface that generates PDF diagrams of schedule and package definitions."
tags:
  - Reference
  - Automation Engineer
  - Schedules
---

# Batch diagram processing

**Theme:** Build  
**Who Is It For?** Automation Engineer

OpCon Deploy includes the capability to create a diagram of either a package or a schedule.

Diagrams of schedules and packages are produced using a command-line interface (CLI). The CLI only creates the diagrams that exist in the configured diagrams directory and displays the full name of the created PDF file.

Diagram.SMAOpConDeployClient supports the following arguments in the CLI:

**-ho**

* Optional argument that indicates if the package diagram should only consist of headers. Default value is complete diagram

**-p**	

* Required argument that consists of the password of the user that is defined in the -u argument 
    * The password must be encrypted using the encryption tool provided by Enterprise Manager

**-pkg**	

* Optional argument that consists of the name of a package that the diagram must be created for
    * Either a package (-pkg) or a schedule (-sch) argument must be present

**-sch**

* Optional argument that consists of the name of a schedule that the diagram must be created for
    * Either a package (-pkg) or a schedule (-sch) argument must be present

**-u**	

* Required argument that defines the user that will perform the action 
* It must be a registered user in the repository 
* During the DEPLOY or SIMULATE actions, a check is made to determine if the user has the appropriate role to access the server defined in the -s argument

**-v**	

* Required argument that defines the version of the schedule or package to create the diagram

## Examples

```
C:\test\deploy\Diagram.SMAOpConDeployClient.exe -sch "SCH001" -u admin -v 11 -p lBsC5ohnSf2P7/Ku81FiGw==
```
 
```
C:\test\deploy\Diagram.SMAOpConDeployClient.exe -pkg "PKG001" -u admin -v 15 -p lBsC5ohnSf2P7/Ku81FiGw==
```
 
```
C:\test\deploy\Diagram.SMAOpConDeployClient.exe -pkg "PKG001" -u admin -v 15 -ho -p lBsC5ohnSf2P7/Ku81FiGw==
```
 

The above examples show how the Diagram.SMAOpConDeployClient program can be used to create diagrams:

* In the first example, a diagram of schedule SCH001 version 11 is created
* In the second example, a complete diagram of package PKG001 version 15 is created
* In the third example, a headers only diagram of package PKG001 version 15 is created

## Exception handling

| Error or symptom | Meaning | How to fix it |
|---|---|---|
| Diagram is not created and no output file is displayed | The `diagramDirectory` setting is not configured or the configured directory is not accessible | Verify that the diagram output directory is set in the Deploy configuration and that the account running the CLI has read/write access to that directory |
| Processing stops with a "not found" error for the schedule or package | The schedule or package name supplied via `-sch` or `-pkg` does not exist in the Deploy repository for the version specified with `-v` | Confirm the name and version number are correct and that the record exists in the Deploy repository |
| PDF generation fails | The diagram process encountered an error while writing the PDF file, such as insufficient disk space or a permissions issue on the output directory | Check available disk space in the diagram output directory and confirm write permissions for the account running Diagram.SMAOpConDeployClient.exe |

## Key terms

**Diagram processing** — the use of `Diagram.SMAOpConDeployClient.exe` to generate a PDF diagram of a schedule or package definition stored in the Deploy repository; the CLI builds a GraphViz Dot source file from the definition and produces a PDF in the configured diagram output directory.

**diagramDirectory** — the configured output directory where `Diagram.SMAOpConDeployClient.exe` writes the generated PDF files; the directory must exist and be writable before diagram processing can succeed.

**Complete diagram vs Header diagram** — the two diagram types available when generating a package diagram: the complete diagram renders all jobs, dependencies, resources, and thresholds in full detail, while the header diagram shows only schedule folder shapes and container jobs to give a structural overview; for a schedule (non-package), only the complete diagram is available.

**Related topics:**

- [Package and schedule diagram](package-and-schedule-diagram)
- [Batch processing](batch-processing)
