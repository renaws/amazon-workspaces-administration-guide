# Launch a WorkSpace Using a Trusted Domain<a name="launch-workspace-trusted-domain"></a>

Amazon WorkSpaces enables you to provision virtual, cloud\-based Microsoft Windows desktops for your users, known as *WorkSpaces*\.

Amazon WorkSpaces uses directories to store and manage information for your WorkSpaces and users\. For your directory, you can choose from Simple AD, AD Connector, or AWS Directory Service for Microsoft Active Directory \(Enterprise Edition\), also known as Microsoft AD\. In addition, you can establish a trust relationship between your Microsoft AD directory and your on\-premises domain\.

In this tutorial, we launch a WorkSpace that uses a trust relationship\. For tutorials that use the other options, see [Launch a Virtual Desktop Using Amazon WorkSpaces](launch-workspaces-tutorials.md)\.


+ [Before You Begin](#prereqs-trusted-domain)
+ [Step 1: Establish a Trust Relationship](#create-trust-relationship)
+ [Step 2: Create a WorkSpace](#create-workspace-trusted-domain)
+ [Step 3: Connect to the WorkSpace](#connect-workspace-trusted-domain)
+ [Next Steps](#next-steps-trusted-domain)

## Before You Begin<a name="prereqs-trusted-domain"></a>

+ Amazon WorkSpaces is not available in every region\. Verify the supported regions and select a region for your WorkSpaces\. For more information about the supported regions, see [Amazon WorkSpaces Pricing by AWS Region](https://aws.amazon.com/workspaces/pricing/)\.

+ When you launch a WorkSpace, you must select a WorkSpace bundle\. A bundle is a combination of storage, compute, and software resources\. For more information, see [Amazon WorkSpaces Bundles](https://aws.amazon.com/workspaces/details/#Amazon_WorkSpaces_Bundles)\.

## Step 1: Establish a Trust Relationship<a name="create-trust-relationship"></a>

**To set up the trust relationship**

1. Set up Microsoft AD in your virtual private cloud \(VPC\)\. For more information, see [How to Create a Microsoft AD directory](http://docs.aws.amazon.com/directoryservice/latest/admin-guide/create_managed_ad.html) in the *AWS Directory Service Administration Guide*\.

1. Create a trust relationship between your Microsoft AD and your on\-premises domain\. Ensure that the trust is configured as a two\-way trust\. For more information, see [Tutorial: Create a Trust Relationship Between Your Microsoft AD and Your On\-Premises Domain](http://docs.aws.amazon.com/directoryservice/latest/admin-guide/tutorial_setup_trust.html) in the *AWS Directory Service Administration Guide*\.

## Step 2: Create a WorkSpace<a name="create-workspace-trusted-domain"></a>

After you establish a trust relationship between your AWS Microsoft AD and your on\-premises Microsoft Active Directory domain, you can provision WorkSpaces for users in the on\-premises domain\.

Note that you must ensure that GPO settings are replicated across domains before you can apply them to Amazon WorkSpaces\.

**To launch workspaces for users in a trusted on\-premises domain**

1. Open the Amazon WorkSpaces console at [https://console\.aws\.amazon\.com/workspaces/](https://console.aws.amazon.com/workspaces/)\.

1. In the navigation pane, choose **WorkSpaces**\.

1. Choose **Launch WorkSpaces**\.

1. On the **Select a Directory** page, choose the directory that you just registered and then choose **Next Step**\.

1. On the **Identify Users** page, do the following:

   1. For **Select trust from forest**, select the trust relationship that you created\.

   1. Select the users from the on\-premises domain and then choose **Add Selected**\.

   1. Choose **Next Step**\.

1. Select the bundle to be used for the WorkSpaces and then choose **Next Step**\.

1. Choose the running mode, choose the encryption settings, and configure any tags\. When you are finished, choose **Next Step**\.

1. Choose **Launch WorkSpaces**\. Note that it can take up to 20 minutes for the WorkSpaces to become available, and up to 40 minutes if encryption is enabled\. The initial status of the WorkSpace is `PENDING`\. When the launch is complete, the status is `AVAILABLE` and an invitation is sent to the email address for each user\.

## Step 3: Connect to the WorkSpace<a name="connect-workspace-trusted-domain"></a>

After you receive the invitation email, you can connect to your WorkSpace\. Users can enter their user names as *username*, *corp*\\*username*, or *corp\.example\.com*\\*username*\)\.

**To connect to the WorkSpace**

1. Open the link in the invitation email\. When prompted, type a password and activate the user\. Remember this password as you will need it to sign in to your WorkSpace\.
**Note**  
Passwords are case\-sensitive and must be between 8 and 64 characters in length, inclusive\. Passwords must contain at least one character from three of the following categories: lowercase letters \(a\-z\), uppercase letters \(A\-Z\), numbers \(0\-9\), and \~\!@\#$%^&\*\_\-\+=`|\\\(\)\{\}\[\]:;"'<>,\.?/\.

1. When prompted, download one of the client applications or launch Web Access\.

   If you aren't prompted and you haven't installed a client application already, open [http://clients\.amazonworkspaces\.com/](http://clients.amazonworkspaces.com/) and follow the directions\.

1. Start the client, enter the registration code from the invitation email, and choose **Register**\.

1. When prompted to sign in, type the username and password for the user, and then choose **Sign In**\.

1. \(Optional\) When prompted to save your credentials, choose **Yes**\.

## Next Steps<a name="next-steps-trusted-domain"></a>

You can continue to customize the WorkSpace that you just created\. For example, you can install software and then create a custom bundle from your WorkSpace\. If you are finished with your WorkSpace, you can delete it\. For more information, see the following documentation\.

+ [Create a Custom WorkSpaces Bundle](create-custom-bundle.md)

+ [Administer Your WorkSpaces](administer-workspaces.md)

+ [Manage Directories for Amazon WorkSpaces](manage-workspaces-directory.md)

+ [Delete a WorkSpace](delete-workspaces.md)