---
title: "Reporting Services SoapException クラス |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/16/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- exceptions [Reporting Services], SoapException class
- SoapException class
ms.assetid: 2cec49ee-20b1-40eb-a75b-0908d9c05b34
caps.latest.revision: 33
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: e24a518bee7b192505fc93ad26d4345f9d710143
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="reporting-services-soapexception-class"></a>Reporting Services SoapException クラス
  発生が予想される [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のエラーには、対処が必要です。 たとえば、ユーザーにフォルダーの作成を要求するアプリケーションでは、ユーザーが既に存在するフォルダーを作成する可能性があります。 開発者としては、アプリケーションのフォルダー名フィールドとパス フィールドにユーザーが入力する内容を制限することはできません。ただし、既に存在するアイテムをユーザーが誤って作成しようとしたとき、どのように対処するかを指定することは可能です。  
  
 特定のエラー条件を検出しやすく[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]例外のエラー コードを分類し、プロパティを使用して、エラーの分類を返します、 **SoapException**クラスです。 詳細については、「SoapException クラス」を参照してください、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK のドキュメントです。  
  
 次の表のパブリック プロパティ、 **SoapException**クラスです。  
  
|パブリック プロパティ|Description|  
|---------------------|-----------------|  
|**アクター**|例外の原因となったコード。 値は Web サービス メソッドへの URL です。|  
|**詳細**|アプリケーション固有のエラー情報。 この値は、レポート サーバーによって XML 形式で設定されます。 詳細については、次を参照してください。 [Detail プロパティ](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/detail-property.md)と[特定のエラーを処理する詳細プロパティを使用して](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/using-the-detail-property-to-handle-specific-errors.md)です。|  
|**HelpLink**|エラーに関連付けられたヘルプ ファイルへの URL または URN。 通常、この値は、Web サービスによって [!INCLUDE[msCoName](../../../includes/msconame-md.md)] ヘルプとサポート サイトの URL に設定されます。 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]のエラーが発生すると、レポート サーバーのヘルプの設定を複数のヘルプ リンクをサポートしているリンクの一部としての情報、**詳細**プロパティです。 詳細については、次を参照してください。 [HelpLink 要素](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/helplink-element.md)です。|  
|**メッセージ**|エラーを説明するローカライズされたメッセージ。 このテキストはアプリケーションの UI に表示される場合があります。|  
  
## <a name="see-also"></a>参照  
 [Reporting Services での例外処理の概要](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [SoapException エラー テーブル](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/soapexception-errors-table.md)  
  
  
