---
title: "Reporting Services 例外処理のベスト プラクティス |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
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
- exceptions [Reporting Services], best practices
ms.assetid: 72fecf28-f02e-4338-b50f-0b21f520302d
caps.latest.revision: 34
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: 8f6546605af6bb6c23b6b380fbaf7042d093addf
ms.contentlocale: ja-jp
ms.lasthandoff: 08/12/2017

---
# <a name="best-practices-for-reporting-services-exception-handling"></a>Reporting Services 例外処理のベスト プラクティス
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] アプリケーションを開発する場合、例外の発生を排除または削減するための方法がいくつかあります。 例外が発生した場合に、明確かつ簡潔なエラー メッセージをユーザーに提供し、アプリケーションの異常終了を防止するために十分な例外処理を追加してください。  
  
 要求をレポート サーバー Web サービスに送信するアプリケーションは、次のことを実行する必要があります。  
  
-   無効な要求をできる限り多く防ぐことによって、例外の発生を回避します。  
  
-   例外をキャッチし、可能な場合は特定のエラー処理コードを提供します。  
  
-   例外をスローしないエラーを処理します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
|トピック|Description|  
|-----------|-----------------|  
|[無効な要求の回避](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/preventing-invalid-requests.md)|無効な要求がレポート サーバーに送信されるのを回避する技術について説明します。|  
|[Try ブロックと Catch ブロックの使用](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/using-try-and-catch-blocks.md)|try ブロックと catch ブロックを使用して、アプリケーションの信頼性を高める方法について説明します。|  
|[例外が発生しない警告および状況の処理](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/handling-warnings-and-cases-that-do-not-cause-exceptions.md)|[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] によってスローされない例外となるエラーの処理方法について説明します。|  
|[Detail プロパティを使用して、特定のエラーを処理するには](../../../reporting-services/report-server-web-service-net-framework-exception-handling/best-practices/using-the-detail-property-to-handle-specific-errors.md)|使用してプログラムによって特定のエラーを処理する方法について説明します、**詳細**のプロパティ、 **SoapException**オブジェクト。|  
  
## <a name="see-also"></a>参照  
 [Detail プロパティ](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/detail-property.md)   
 [Reporting Services での例外処理の概要](../../../reporting-services/report-server-web-service-net-framework-exception-handling/introducing-exception-handling-in-reporting-services.md)   
 [Reporting Services SoapException クラス](../../../reporting-services/report-server-web-service-net-framework-exception-handling/soapexception-class/reporting-services-soapexception-class.md)  
  
  
