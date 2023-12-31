
## Reference : 
- URL https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/redshift_cluster#example-usage


## Argument Reference
The following arguments are supported:
|Argument|Required|Description|
|:---:|:---:|---|
|cluster_identifier|(Required)|The Cluster Identifier. Must be a lower case string.|
|database_name|(Optional)|The name of the first database to be created when the cluster is created. If you do not provide a name, Amazon Redshift will create a default database called dev.|
|default_iam_role_arn|(Optional)|The Amazon Resource Name (ARN) for the IAM role that was set as default for the cluster when the cluster was created.|
|node_type|(Required)|The node type to be provisioned for the cluster.|
|cluster_type|(Optional)|The cluster type to use. Either single-node or multi-node.|
|master_password|(Required unless a snapshot_identifier is provided)|Password for the master DB user. Note that this may show up in logs, and it will be stored in the state file. Password must contain at least 8 chars and contain at least one uppercase letter, one lowercase letter, and one number.|
|master_username|(Required unless a snapshot_identifier is provided)|Username for the master DB user.|
|vpc_security_group_ids|(Optional)|A list of Virtual Private Cloud (VPC) security groups to be associated with the cluster.|
|cluster_subnet_group_name|(Optional)|The name of a cluster subnet group to be associated with this cluster. If this parameter is not provided the resulting cluster will be deployed outside virtual private cloud (VPC).|
|availability_zone|(Optional)|The EC2 Availability Zone (AZ) in which you want Amazon Redshift to provision the cluster. For example, if you have several EC2 instances running in a specific Availability Zone, then you might want the cluster to be provisioned in the same zone in order to decrease network latency. Can only be changed if availability_zone_relocation_enabled is true.|
|availability_zone_relocation_enabled|(Optional)|If true, the cluster can be relocated to another availabity zone, either automatically by AWS or when requested. Default is false. Available for use on clusters from the RA3 instance family.|
|preferred_maintenance_window|(Optional)|The weekly time range (in UTC) during which automated cluster maintenance can occur. Format: dddhh24mi-dddhh24mi|
|cluster_parameter_group_name|(Optional)|The name of the parameter group to be associated with this cluster.|
|automated_snapshot_retention_period|(Optional)|The number of days that automated snapshots are retained. If the value is 0, automated snapshots are disabled. Even if automated snapshots are disabled, you can still create manual snapshots when you want with create-cluster-snapshot. Default is 1.|
|port|(Optional)|The port number on which the cluster accepts incoming connections. Valid values are between 1115 and 65535. The cluster is accessible only via the JDBC and ODBC connection strings. Part of the connection string requires the port on which the cluster will listen for incoming connections. Default port is 5439.|
|cluster_version|(Optional)|The version of the Amazon Redshift engine software that you want to deploy on the cluster. The version selected runs on all the nodes in the cluster.|
|allow_version_upgrade|(Optional)|If true , major version upgrades can be applied during the maintenance window to the Amazon Redshift engine that is running on the cluster. Default is true.|
|apply_immediately|(Optional)|Specifies whether any cluster modifications are applied immediately, or during the next maintenance window. Default is false.|
|aqua_configuration_status|(Optional, Deprecated)|The value represents how the cluster is configured to use AQUA (Advanced Query Accelerator) after the cluster is restored. No longer supported by the AWS API. Always returns auto.|
|number_of_nodes|(Optional)|The number of compute nodes in the cluster. This parameter is required when the ClusterType parameter is specified as multi-node. Default is 1.|
|publicly_accessible|(Optional)|If true, the cluster can be accessed from a public network. Default is true.|
|encrypted|(Optional)|If true , the data in the cluster is encrypted at rest.|
|enhanced_vpc_routing|(Optional)|If true , enhanced VPC routing is enabled.|
|kms_key_id|(Optional)|The ARN for the KMS encryption key. When specifying kms_key_id, encrypted needs to be set to true.|
|elastic_ip|(Optional)|The Elastic IP (EIP) address for the cluster.|
|skip_final_snapshot|(Optional)|Determines whether a final snapshot of the cluster is created before Amazon Redshift deletes the cluster. If true , a final cluster snapshot is not created. If false , a final cluster snapshot is created before the cluster is deleted. Default is false.|
|final_snapshot_identifier|(Optional)|The identifier of the final snapshot that is to be created immediately before deleting the cluster. If this parameter is provided, skip_final_snapshot must be false.|
|snapshot_identifier|(Optional)|The name of the snapshot from which to create the new cluster.|
|snapshot_cluster_identifier|(Optional)|The name of the cluster the source snapshot was created from.|
|owner_account|(Optional)|The AWS customer account used to create or copy the snapshot. Required if you are restoring a snapshot you do not own, optional if you own the snapshot.|
|iam_roles|(Optional)|A list of IAM Role ARNs to associate with the cluster. A Maximum of 10 can be associated to the cluster at any time.|
|logging|(Optional)|Logging, documented below.|
|maintenance_track_name|(Optional)|The name of the maintenance track for the restored cluster. When you take a snapshot, the snapshot inherits the MaintenanceTrack value from the cluster. The snapshot might be on a different track than the cluster that was the source for the snapshot. For example, suppose that you take a snapshot of a cluster that is on the current track and then change the cluster to be on the trailing track. In this case, the snapshot and the source cluster are on different tracks. Default value is current.|
|manual_snapshot_retention_period|(Optional)|The default number of days to retain a manual snapshot. If the value is -1, the snapshot is retained indefinitely. This setting doesn't change the retention period of existing snapshots. Valid values are between -1 and 3653. Default value is -1.|
|snapshot_copy|(Optional)|Configuration of automatic copy of snapshots from one region to another. Documented below.|
|tags|(Optional)|A map of tags to assign to the resource. If configured with a provider default_tags configuration block present, tags with matching keys will overwrite those defined at the provider-level.|
---