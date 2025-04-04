---
title: Power Query Adobe Analytics connector
description: Provides basic information and prerequisites for the connector, descriptions of the optional input parameters, and discusses limitations and issues you might encounter.
author: bezhan-msft
ms.topic: conceptual
ms.date: 1/18/2022
ms.author: bezhan
---

# Adobe Analytics
 
## Summary

| Item | Description |
| ---- | ----------- |
| Release State | General Availability |
| Products | Power BI (datasets)<br/>Power BI (Dataflows)<br/>Power Apps (Dataflows)<br/>Customer Insights (Dataflows) |
| Authentication Types Supported | Organizational account |
| Function Reference Documentation | [AdobeAnalytics.Cubes](/powerquery-m/adobeanalytics-cubes) |
| | |
## Prerequisites
Before you can sign in to Adobe Analytics, you must have an Adobe Analytics account (username/password).

 
## Capabilities Supported
* Import

## Connect to Adobe Analytics data

To connect to Adobe Analytics data:

1. Select **Get Data** from the **Home** ribbon in Power BI Desktop. Select **Online Services** from the categories on the left, select **Adobe Analytics**, and then select **Connect**.

   ![Get Data from Adobe Analytics.](./media/adobe-analytics/get-aa-data.png)

2. If this is the first time you're getting data through the Adobe Analytics connector, a third-party notice will be displayed. Select **Don't warn me again with this connector** if you don't want this message to be displayed again, and then select **Continue**.

3. To sign in to your Adobe Analytics account, select **Sign in**.

   ![Select sign in button.](./media/adobe-analytics/sign-in.png)


4. In the Adobe Analytics window that appears, provide your credentials to sign in to your Adobe Analytics account. You can either supply a username (which is usually an email address), or select **Continue with Google** or **Continue with Facebook**.

   ![Sign in to Adobe Analytics.](./media/adobe-analytics/adobe-sign-in.png)

   If you entered an email address, select **Continue**.

5. Enter your Adobe Analytics password and select **Continue**.

   ![Enter your password.](./media/adobe-analytics/enter-password.png)

6. Once you've successfully signed in, select **Connect**.

   ![Signed in and ready to connect.](./media/adobe-analytics/signed-in.png)

Once the connection is established, you can preview and select multiple dimensions and measures within the **Navigator** dialog box to create a single tabular output. 

![Select data using Navigator.](./media/adobe-analytics/navigator-view.png)

You can also provide any optional input parameters required for the selected items. For more information about these parameters, see [Optional input parameters](#optional-input-parameters).

You can **Load** the selected table, which brings the entire table into Power BI Desktop, or you can select **Transform Data** to edit the query, which opens Power Query Editor. You can then filter and refine the set of data you want to use, and then load that refined set of data into Power BI Desktop.

![Load or transform data.](./media/adobe-analytics/button-select.png)

## Optional input parameters

When you've selected the Adobe Analytics data you want to load or transform in the Power Query **Navigator** dialog box, you can also limit the amount of data by selecting a set of optional input parameters. 

![Optional input parameters.](./media/adobe-analytics/navigator-options.png)

These input parameters are:

* Date Range&mdash;filter with a reporting range between a start date and an end date that you set.

* Segment&mdash;filter the data based on all segments contained in the data, or only those segments you select. To change the list of segments, select the ellipsis to the right of the **Segment** list box, then choose the segments you want. By default, all segments are included in the data.

   ![Select the list of segments.](./media/adobe-analytics/segment-select.png)

* Top&mdash;filter the data based on the top items for the dimension. You can enter a value in the **Top** text box, or select the ellipsis next to the text box to select some default values. By default, all items are selected.

* Dimension&mdash;filter the data based on the selected dimension. By default, all dimensions are selected. Custom Adobe dimension filters are not currently supported in the Power Query user interface, but can be defined by hand as M parameters in the query. For more information, see [Using Query Parameters in Power BI Desktop](../power-query-query-parameters.md).

## Limitations and issues

You should be aware of the following limitations and issues associated with accessing Adobe Analytics data.

* Adobe Analytics has a built-in limit of 50 K rows returned per API call. 

* If the number of API calls exceeds four per second, a warning will be issued. If the number exceeds five per second, an error message will be returned. For more information about these limits and the associated messages, see [Web Services Error Codes](https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/getting-started/c_Web_Services_Error_Codes.md#web-services-error-codes).

* The API request timeout through adobe.io is currently 60 seconds.

* The default rate limit for an Adobe Analytics Company is 120 requests per minute per user (the limit is enforced as 12 requests every 6 seconds).

Import from Adobe Analytics will stop and display an error message whenever the Adobe Analytics connector hits any of the API limits listed above.

When accessing your data using the Adobe Analytics connector, follow the guidelines provided under the [Best Practices](https://www.adobe.io/apis/experiencecloud/analytics/docs.html#!AdobeDocs/analytics-2.0-apis/master/reporting-guide.md) heading.

For additional guidelines on accessing Adobe Analytics data, see [Recommended usage guidelines](https://helpx.adobe.com/analytics/kb/recommended-usage-guidelines.html).

## Next steps

You may also find the following Adobe Analytics information useful:

* [Adobe Analytics 1.4 APIs](https://github.com/AdobeDocs/analytics-1.4-apis)
* [Adobe Analytics Reporting API](https://github.com/AdobeDocs/analytics-1.4-apis/tree/master/docs/reporting-api)
   * [Metrics](https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/reporting-api/metrics.md)
   * [Elements](https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/reporting-api/elements.md)
   * [Segments](https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/segments-api/data_types/r_segment.md)
* [GetReportSuites](https://github.com/AdobeDocs/analytics-1.4-apis/blob/master/docs/admin-api/methods/company/r_GetReportSuites.md)
* [Adobe Analytics support](https://helpx.adobe.com/support/analytics.html)