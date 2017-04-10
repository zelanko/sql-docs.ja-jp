---
title: "レポート定義スキーマのバージョンを確認する (SSRS) | Microsoft Docs"
ms.custom: ""
ms.date: "03/15/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "XML スキーマ [Reporting Services]"
  - "レポート定義言語, XML スキーマ"
  - "スキーマ [Reporting Services]"
ms.assetid: 67954419-1b61-4481-a3b9-23b4ba7a5624
caps.latest.revision: 15
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 15
---
# レポート定義スキーマのバージョンを確認する (SSRS)
  レポート定義ファイルでは、rdl ファイルの検証に使用されるレポート定義スキーマのバージョンに対応して、RDL 名前空間が指定されます。 以前の名前空間に対応するレポートが作成済みの場合、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] のレポート デザイナーやレポート ビルダーなどのレポート作成環境で .rdl ファイルを開くと、バックアップ ファイルが自動的に作成され、レポートが現在の名前空間にアップグレードされます。 アップグレードされたレポート定義を保存すると、変換された .rdl ファイルが保存されることになります。 これは、レポート定義をアップグレードする唯一の方法です。 レポート定義そのものはレポート サーバーでアップグレードされません。 コンパイル済みレポートが、レポート サーバーで自動的にアップグレードされます。 詳細については、「 [Upgrade Reports](../../reporting-services/install-windows/upgrade-reports.md)」を参照してください。  
  
### レポートの RDL スキーマのバージョンを確認する方法  
  
1.  メモ帳や、XML を表示できる XML Notepad 2007 などのアプリケーションでレポートの .rdl ファイルを開きます。  
  
     スキーマ名前空間は XML の Report 要素で指定されます。 たとえば、次の Report 要素では、レポート デザイナーの名前空間とレポート定義の名前空間が指定されています。  
  
    ```  
    <Report xmlns:rd=http://schemas.microsoft.com/SQLServer/reporting/reportdesigner   
    xmlns="http://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition">  
    ```  
  
     レポート定義の名前空間は、`http://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition` という URL で指定されています。  
  
### レポート デザイナーの RDL スキーマのバージョンを確認する方法  
  
1.  新しいプロジェクトを開きます。 選択したプロジェクトのバージョンにより、RDL スキーマのバージョンが決まります。 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、複数のスキーマ バージョンがサポートされています。 詳細については、「[SQL Server データ ツールの配置およびバージョン サポート &#40;SSRS&#41;](../../reporting-services/tools/deployment-and-version-support-in-sql-server-data-tools-ssrs.md)」を参照してください。  
  
2.  **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。 **[新しい項目の追加]** ダイアログ ボックスが表示されます。  
  
3.  **[テンプレート]** ペインで **[レポート]** をクリックします。  
  
4.  **[名前]** にレポートの名前を入力するか、既定の名前をそのまま使用します。  
  
5.  **[追加]**をクリックします。 レポート デザイナーの [デザイン] ビューに新しい空のレポートが表示されます。  
  
6.  **[表示]** メニューの **[コード]** をクリックします。 レポート定義が XML ファイルとして表示されます。  
  
     スキーマ名前空間は XML の Report 要素で指定されます。 たとえば、次の Report 要素では、レポート デザイナーの名前空間とレポート定義の名前空間が指定されています。  
  
    ```  
    <Report xmlns:rd=http://schemas.microsoft.com/SQLServer/reporting/reportdesigner  
    xmlns="http://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition">  
    ```  
  
     レポート定義の名前空間は、次の URL で指定されています。 `http://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition`  
  
### レポート サーバー上で RDL スキーマのバージョンを確認する方法  
  
-   レポート マネージャーで、レポート サーバーの URL を入力します。 たとえば、次の URL はローカル コンピューターのレポート サーバーを指定しています。  
  
     `http://localhost/reportserver/reportdefinition.xsd`  
  
     .xsd ファイルがブラウザーに表示されます。  
  
     スキーマ名前空間は XML の schema 要素で指定されます。 たとえば、次の schema 要素では、[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] によって内部的に使用される targetNamespace 参照、スキーマ自体 (xsd) の xsd 参照、およびレポート定義参照の 3 つの名前空間が指定されています。  
  
    ```  
    <xsd:schema   
    targetNamespace="http://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition"   
    xmlns:xsd="http://www.w3.org/2001/XMLSchema"   
    xmlns="http://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition"   
    elementFormDefault="qualified">  
    ```  
  
     レポート定義の名前空間は、次の URL で指定されています。 `http://schemas.microsoft.com/sqlserver/reporting/2009/01/reportdefinition`  
  
## 参照  
 [レポートのアップグレード](../../reporting-services/install-windows/upgrade-reports.md)   
 [レポート定義言語 (SSRS)](../../reporting-services/reports/report-definition-language-ssrs.md)  
  
  