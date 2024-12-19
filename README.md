# Visualize Amazon WorkSpaces Utilization with Amazon QuickSight

## Overview

This solution provides a comprehensive guide to visualizing Amazon WorkSpaces utilization data using Amazon QuickSight. It helps customers gain insights into billable hours, running modes, bundle types, and AWS regions, enabling cost optimization and better efficiency.

![Architecture Diagram](/images/Figure1.png "Architecture")

## Features

- **Cost Optimization:** Identify underutilized WorkSpaces and optimize running modes to reduce costs.
- **Usage Analysis:** Assess trends and forecast utilization for better planning.
- **Bundle Assessment:** Evaluate the suitability of selected WorkSpace bundles.

## Architecture

The solution leverages:

- **Cost Optimizer for Amazon WorkSpaces:** Collects and analyzes usage data.
- **AWS Lambda:** Automates data refresh and transfer to Amazon S3.
- **Amazon S3:** Stores utilization data.
- **Amazon QuickSight:** Visualizes data for deeper insights.

## Prerequisites

- An AWS account with QuickSight enabled.
- Cost Optimizer for Amazon WorkSpaces deployed in "Dry Run Mode."
- Sufficient SPICE capacity in the AWS region.
- Permissions for:
  - Amazon S3: `s3:GetBucketLocation`, `s3:ListBucket`, `s3:GetObject`.
  - AWS Lambda: `lambda:InvokeFunction`.
  - Amazon QuickSight: `quicksight:ListDataSources`, `quicksight:ListDataSets`, `quicksight:CreateAnalysis`, `quicksight:DescribeAnalysis`.
  - AWS CloudFormation: `cloudformation:DescribeStacks`, `cloudformation:ListStackResources`.

## Deployment

### 1. Ensure Cost Optimizer Deployment
Deploy or update the latest Cost Optimizer for Amazon WorkSpaces and collect utilization data.

### 2. Deploy Foundational Infrastructure
Use the `1_foundational_infrastructure.yaml` CloudFormation template to set up S3 buckets and permissions.

### 3. Grant QuickSight Access
Configure Amazon S3 permissions in QuickSight for access to utilization data.

### 4. Deploy QuickSight Data Components
Use the `2_quicksight_data_components.yaml` template to create data sources and datasets in QuickSight.

### 5. (Optional) Configure Region Mapping
Map directory IDs to human-readable region names using a custom CSV file.

### 6. Visualize Data
Build analyses and dashboards in QuickSight to gain actionable insights.

## Example Visualizations

### Tables
Display WorkSpaces utilization details with conditional formatting.

### Pie Charts
Analyze WorkSpaces distribution by:
- Region
- Bundle type
- Running mode

### Bar Charts
Compare WorkSpaces billable hours against breakeven points.

## Cleanup

To remove resources:
1. Empty the WorkSpaces data S3 bucket.
2. Delete the deployed CloudFormation stacks.
3. If necessary, delete your QuickSight subscription.

## Cost Estimate

You are responsible for the cost of AWS services used while running this solution. As of December 2024, the cost for running this solution in the US East (N. Virginia) Region is approximately **$5**, plus an Amazon QuickSight subscription fee.

## Security

For more details, see [CONTRIBUTING](./CONTRIBUTING.md).

## License

This solution is licensed under the MIT-0 License. See the [LICENSE](./LICENSE) file.
