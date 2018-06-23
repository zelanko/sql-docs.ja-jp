---
title: URL でデバイス情報設定を指定する | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- device information settings [Reporting Services], URLs
- URL access [Reporting Services], device information settings
ms.assetid: cb7f7577-c6a8-4e6f-8e60-5ec0760f29c3
caps.latest.revision: 32
author: markingmyname
ms.author: maghan
manager: mblythe
ms.openlocfilehash: dacc371522447f3af056fcde3a48b6d4fca886c9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36177917"
---
# <a name="specify-device-information-settings-in-a-url"></a>URL でデバイス情報設定を指定する
  デバイス情報設定は、表示拡張機能に渡すパラメーターのことです。 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] レポート サーバー Web サービスのメソッドを使用してレポートを表示する場合は、`DeviceInfo` XML 要素を入力パラメーターとして渡す必要があります。 子要素、`DeviceInfo`要素は、さまざまな表示拡張機能のデバイス情報設定に固有です。 *rc:tag=value* パラメーターの文字列を使用することによって、デバイス情報設定を URL に含めることができます。ここでは、 *tag* はアクセス先デバイス情報設定要素の名前です。 デバイス情報設定の詳細については[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]を参照してください[表示拡張機能にデバイス情報設定を渡す](report-server-web-service/net-framework/passing-device-information-settings-to-rendering-extensions.md)です。  
  
## <a name="example"></a>例  
 次の例では、画像表示拡張機能の *OutputFormat* デバイス情報設定を使用して、指定されたレポートの形式を JPEG に設定します。読みやすいように改行しています。  
  
```  
http://servername/reportserver?/SampleReports  
/Employee Sales Summary&EmployeeID=38&rs:  
Command=Render&rs:Format=IMAGE&rc:OutputFormat=JPEG  
```  
  
## <a name="see-also"></a>参照  
 [URL アクセス&#40;SSRS&#41;](url-access-ssrs.md)   
 [URL アクセス パラメーター リファレンス](url-access-parameter-reference.md)  
  
  