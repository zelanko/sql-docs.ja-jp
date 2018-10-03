---
title: カスタム レポート アイテムを配置する方法 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- custom report items, deploying
ms.assetid: 80e97b0d-e355-4240-aebd-08cbc84089ed
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 48e55cfb3eb754af540ca4eb4d19ae415d396f60
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48175872"
---
# <a name="how-to-deploy-a-custom-report-item"></a>カスタム レポート アイテムを配置する方法
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] でカスタム レポート アイテムを配置するには、レポート サーバー構成ファイルを変更し、デザイン時と実行時のコンポーネント アセンブリをレポート デザイナーとレポート サーバーの両方に対する適切なアプリケーション フォルダーにコピーする必要があります。  
  
### <a name="to-deploy-a-custom-report-item"></a>カスタム レポート アイテムを配置するには  
  
1.  Rsreportdesigner.config ファイルを編集して、デザイナーで使用するカスタム レポート アイテムの実行時とデザイン時のコンポーネントを構成します。 `ReportItemName` エントリは `CustomReportItemAttribute` クラス内で使用される `CustomReportItemDesigner` 属性と一致する必要があることに注意してください。 以下に例を示します。  
  
    ```  
    <ReportItems>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsCRI,PolygonsCRI"/>  
    </ReportItems>  
    <ReportItemDesigner>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsDesigner, PolygonsDesigner" />  
    </ReportItemDesigner>  
    <ReportItemConverter>  
       <Converter Source="Chart" Target="Polygons" Type="PolygonsCRI.PolygonsConverter, PolygonsDesigner" />  
    </ReportItemConverter>  
    ```  
  
2.  Rsreportserver.config ファイルを編集して、カスタム レポート アイテムの実行時コンポーネントを登録します。 以下に例を示します。  
  
    ```  
    <ReportItems>  
       <ReportItem Name="Polygons" Type="PolygonsCRI.PolygonsCRI,PolygonsCRI"/>  
    </ReportItems>  
    ```  
  
3.  Rsssrvpolicy.config ファイルを編集して、カスタム レポート アイテムに適切な権限を許可する `CodeGroup` を追加します。 以下に例を示します。  
  
    ```  
    <CodeGroup   
       class="UnionCodeGroup"   
       version="1"   
       PermissionSetName="FullTrust"  
       Description="This code group grants MyCustomReportItem.dll FullTrust permission. ">  
       <IMembershipCondition   
          class="UrlMembershipCondition"  
          version="1"  
       Url="C:\Program Files\Microsoft SQL Server\ MSRS10_50.SQLSERVER\Reporting Services\ReportServer\bin\MyCustomReportItem.dll" />  
    </CodeGroup>  
    ```  
  
4.  カスタム レポート アイテムの実行時コンポーネント DLL を、%ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies ディレクトリと \Program Files\Microsoft SQL Server\MSRS10_50.SQLSERVER\Reporting Services\ReportServer\bin ディレクトリにコピーします。  
  
5.  カスタム レポート アイテムのデザイン時コンポーネント DLL を %ProgramFiles%\Microsoft Visual Studio 9.0\Common7\IDE\PrivateAssemblies ディレクトリにコピーします。  
  
## <a name="see-also"></a>参照  
 [Reporting Services 構成ファイル](../report-server/reporting-services-configuration-files.md)   
 [カスタム レポート アイテムのクラス ライブラリ](custom-report-item-class-libraries.md)  
  
  
