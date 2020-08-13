---
title: URL でレポート パラメーターの言語を設定する | Microsoft Docs
description: rs:ParameterLanguage URL アクセス パラメーターを使用して、URL でレポート パラメーターの言語を設定する方法について説明します。
ms.date: 03/01/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: reporting-services
ms.topic: conceptual
helpviewer_keywords:
- overriding report language settings
- report servers [Reporting Services], language settings
- languages [Reporting Services]
- URL access [Reporting Services], language overrides
- international considerations [Reporting Services]
- global considerations [Reporting Services]
ms.assetid: e1ccf22f-80d6-45bc-aae0-f5f263275092
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 5972235f37a8cc10968d68a614bab00f3ca9a556
ms.sourcegitcommit: 216f377451e53874718ae1645a2611cdb198808a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/28/2020
ms.locfileid: "87245709"
---
# <a name="set-the-language-for-report-parameters-in-a-url"></a>URL でレポート パラメーターの言語を設定する
  *rs:ParameterLanguage* URL アクセス パラメーターは、カルチャが特定されたレポート パラメーター (日付、時刻、通貨、数値など) がブラウザーの言語を使用して解釈されるという問題を軽減します。 *rs:ParameterLanguage*を使用すると、URL はブラウザーとは無関係に解釈されるようになります。 たとえば、レポート サーバーの地域がドイツ語に設定されている場合、ユーザーが [英語 (U.S.)] に設定されているブラウザーを使用してレポートの URL にアクセスすると、レポート サーバーに渡されるパラメーター値は間違って解釈されます。  
  
 レポートには次の URL を検討してください。  
  
```  
https://myrshost/Reportserver?/SampleReports/Product+Line+Sales&rs:Command=Render&StartDate=4/10/2008&EndDate=11/10/2008  
```  
  
 上記の場合、カルチャ "de-de" で実行されているサーバーでは、電子メール サブスクリプションまたはハイパーリンクを使用して URL が生成されます。 上記のハイパーリンクは、レポートのパラメーターが、ドイツ語の日付と時刻の標準に基づいた開始日 2008 年 10 月 4 日と終了日 2008 年 10 月 11 日に設定される必要があることを示しています。 この場合に、ユーザーが "en-us" に設定されたブラウザーを使用して URL にアクセスすると、サーバーで解釈される値が、英語 (U.S.) の日付と時刻の標準により、2008 年 4 月 10 日と 2008 年 11 月 10 日になります。 この問題を解決するには、*rs:ParameterLanguage* を使用してパラメーターの解釈をブラウザーの言語より優先させます。  
  
```  
https://myrshost/Reportserver?/SampleReports/Product+Line+Sales&rs:Command=Render&StartDate=4/10/2008&EndDate=11/10/2008&rs:ParameterLanguage=de-DE  
```  
  
 URL アクセス パラメーター **rc:Parameters** には、値 **True** と *False*以外に、値 **Collapsed**を渡すことができるようになりました。 URL に *rc:Parameters*=**Collapsed** を使用すると、HTML ビューアーのパラメーター プロンプト領域が見えないように折りたたまれます。ただし、ユーザーが切り替えることができます。 値を **False** に設定すると、HTML ビューアーのツール バーからパラメーター プロンプト領域が削除され、エンド ユーザーがその領域を使用できません。  
  
## <a name="see-also"></a>参照  
 [URL アクセス (SSRS)](../reporting-services/url-access-ssrs.md)   
 [URL アクセス パラメーター リファレンス](../reporting-services/url-access-parameter-reference.md)  
  
  
