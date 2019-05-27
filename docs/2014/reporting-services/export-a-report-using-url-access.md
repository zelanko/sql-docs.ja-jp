---
title: URL アクセスを使用してレポートをエクスポートする | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- formats [Reporting Services], URL rendering
- URL access [Reporting Services], rendering formats
ms.assetid: 6a3b7fc3-3d91-4d12-8371-42ea12e74517
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 69f340855e37ffde49aec0af096c094a142659d1
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/23/2019
ms.locfileid: "66109191"
---
# <a name="export-a-report-using-url-access"></a>URL アクセスを使用してレポートをエクスポートする
  使用してレポートを表示する形式を指定することができます必要に応じて、 *Rs:format*パラメーター。 たとえば、ネイティブ モードのレポート サーバーから直接レポートの PDF コピーを取得するには、次の URL を使用します。  
  
```  
http://myrshost/ReportServer?/myreport&rs:Format=PDF  
```  
  
 また、SharePoint 統合モードのレポート サーバーから取得するには、次の URL を使用します。  
  
```  
http://myspsite/subsite/_vti_bin/reportserver?http://myspsite/subsite/myrereport.rdl&rs:Format=PDF  
```  
  
 このパラメーターの有効値は、アクセス先レポート サーバーにインストールされているレポート表示拡張機能によって異なります。 一般的な拡張機能は HTML4.0、MHTML、IMAGE、EXCEL、WORD、CSV、PDF、XML、および NULL です。 指定した表示拡張機能がレポート サーバーにインストールされていない場合は、レポートが表示されず、エラーが生成されてブラウザーに表示されます。  
  
 *Format* パラメーターを URL の一部として含めない場合は、レポート サーバーがブラウザーを検出し、適切な HTML 形式でレポートを表示します。  
  
## <a name="see-also"></a>参照  
 [URL アクセス &#40;SSRS&#41;](url-access-ssrs.md)   
 [URL アクセス パラメーター リファレンス](url-access-parameter-reference.md)  
  
  
