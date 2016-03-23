---
title: Add a tab and additional fields to an SAPUI5 app
description: Learn how to add an additional tab, and more data fields to an SAPUI5 app.
tags: [tutorial:product/hcp, tutorial:product/sapui5_web_ide, tutorial:product/mobile, tutorial:product/sap_ui5]
---

## Prerequisites
 - **Proficiency:** Intermediate
 - **Tutorials:** [Insert a currency symbol for display](http://go.sap.com/developer/tutorials/insert-currency-symbol.html)

## Next Steps
 - [Calculate and display a new field in an SAPUI5 app](http://go.sap.com/developer/tutorials/hcp-webide-calculate-new-field.html)

## Details

### You will learn
When you created your initial app, SAP Web IDE template included one tab containing a few fields from the Supplier collection. In this tutorial, you will add another tab using the Web IDE Layout Editor and make a few other changes:


### Time to Complete
**< 5 min**

---

### Change the icon for the Supplier tab

1. Log into your HCP account and open SAP Web IDE in a Google Chrome browser.

    Open th **northwind** project folder and then the **view** folder. Right-click on **Detail.view.xml** and select **Open With > Layout Editor** (you must use Google Chrome to open the Layout Editor).

    ![Layout Editor](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-add-tab/mob3-1_icon_1.png)

2. When the Layout Editor opens, click on the **Supplier** icon. The **Properties and Data pane** will open.

    ![Properties and Data pane](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-add-tab/mob3-1_icon_2.png)

3. In another browser tab, open the [SAPUI5 Icon Explorer](https://openui5.hana.ondemand.com/iconExplorer.html). The Icon Explorer shows all of the icons built into the SAPUI5 library.
    ![UI5 icon explorer](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-add-tab/mob3-1_icon_3.png)

4. Enter `supplier` into the search field, and click on the **supplier** item in the list. The supplier icon is shown in the various UI5 controls.

    ![Supplier icon in the SAPUI5 Icon Explorer](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-add-tab/mob3-1_icon_4.png)

5. To change the current icon in your app, switch back to the Web IDE tab, and enter `sap-icon://supplier` in the **Icon** field. If you tab out of the **Icon** field, the icon will update in the **Layout Editor** view.

    ![changing the icon](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-add-tab/mob3-1_icon_5.png)



### Add a new Details tab to hold other Product data
1. In SAPUI5, a tab is called an **IconTabFilter**. To add one to your app, click on **Container** in the palette pane. Click on the **Icon Tab Filter**, then drag and drop it next to the **Supplier** tab.

    Depending on the path you drag, the new tab may snap to the first (left) spot. You can drag it left and right to place it on the right of the **Supplier IconTabFilter** before letting the mouse button up. You can also release the mouse button to place it where it snaps to first, then click and drag it to the position you want.

    ![adding a new Icon Tab Filter](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-add-tab/mob3-1_tab_1.png)

2. With the new Icon Tab Filter selected, make the following changes in the **Properties and Data pane** and save your changes.

    - **Icon:** `sap-icon://product`
    - **Text:** `Details`
    - **Count:** \< delete the 10 \>
    - **Icon Color:** `Default`

    ![Editing a Icon Tab Filter](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-add-tab/mob3-1_tab_2.png)

### Create a view fragment file for the new tab
Content for a new tab is displayed in a view fragment file.

1. To create a new fragment file, right-click on the **view** folder, and select **New > File**.
    ![create a new file](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-add-tab/mob3-1_fragment_1.png)

2. Enter `ProductDetailInfoForm.fragment.xml` for the new file name and click **OK**.

    ![new file dialog](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-add-tab/mob3-1_fragment_2.png)

3. The new file will open in the editor. Copy the text below, paste it into the new file, right-click in the editor and select **Beautify** (which will re-indent the XML file), then save your changes.

    ```xml
    <core:FragmentDefinition xmlns:core="sap.ui.core" xmlns:f="sap.ui.layout.form" xmlns:l="sap.ui.layout" xmlns="sap.m">

    In addition to the standard XML wrapper, there are a few key items to call out in the source above:

    ![ProductDetailInfoForm.fragment.xml](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-add-tab/mob3-1_fragment_3.png)

4. Open **messageBundle.properties** and replace all of the content of the file with the lines below. These are the strings for the new Product tab, as well as the Supplier tab (which you will edit next).
    ```xml
    masterTitle=Products
    tab_supplier_short_title=Supplier

    Your **messageBundle.properties** file should look like this now.:

    ![messageBundle.properties file](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-add-tab/mob3-1_fragment_4.png)


### Add in other Supplier related data fields to the Supplier tab

1. Open **DetailInfoForm.fragment.xml** (which is the fragment for the **Supplier** tab). In the **f:SimpleForm** element, replace the `title="Supplier"` attribute with `title="{i18n>tab_supplier_sub_title}"` and save your change. Be sure to keep the double quotes. This replaces the string inserted by the template with a reference to one in the **messageBundle.properties** file.

    ![DetailInfoForm title](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-add-tab/mob3-1_supplier_fields_1.png)

2. The Web IDE template inserted three of the fields in the Suppliers Collection (which is linked to the Product Collection). To add in all of the fields available, open **DetailInfoForm.fragment.xml**, and replace all of the content within the `<f:content>` element with the source below, **Beautify** and save your edits.

    ```xml
    <Label text="{i18n>label_SupplierID}"/>

    Your **DetailInfoForm.fragment.xml** file should look like this now:

    ![DetailInfoForm fields](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-add-tab/mob3-1_supplier_fields_2.png)

3. The last step is to add a `content` element to link the new fragment file to the Details Icon Tab Filter. Open **Detail.view.xml**, replace the text within the **items** element with the text below, **Beautify** and save your changes.


    ![content element](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-add-tab/mob3-1_supplier_fields_3.png)

4. Save your changes and reload the preview tab or run the app. Remember, you may need to do a hard reload or clear the cache to see your changes. When the app loads, you will see the additional fields on the **Supplier** tab. Click on the **Product** tab to see the fields there.

    ![Supplier tab](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-add-tab/mob3-1_supplier_fields_4a.png)

    ![products tab](https://raw.githubusercontent.com/SAPDocuments/Tutorials/master/tutorials/hcp-webide-add-tab/mob3-1_supplier_fields_4b.png)

5. You can now re-deploy the app to HCP so you will be able to see your changes on your mobile device.

## Next Steps
 - [Calculate and display a new field in an SAPUI5 app](http://go.sap.com/developer/tutorials/hcp-webide-calculate-new-field.html)