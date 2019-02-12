---
title: 表示拡張機能の削除 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.topic: reference
helpviewer_keywords:
- deleting rendering extensions
- removing rendering extensions
- rendering extensions [Reporting Services], removing
ms.assetid: 2abfebfb-065f-45cc-a904-c914394cf900
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 5c8f55dd0fa663d5516938e9ca39b5a6dc2caed9
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2019
ms.locfileid: "56014632"
---
# <a name="removing-a-rendering-extension"></a>表示拡張機能の削除
  削除する、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]表示拡張機能を削除するだけ、`Extension`要素にある rsreportserver.config ファイルから表示拡張機能の **%ProgramFiles%\Microsoft SQL server \msrs10_50.\< 。インスタンス名 > \reporting**フォルダー。 レポート デザイナーとレポート サーバーのエントリを作成した場合は、削除、`Extension`要素から、 [RSReportDesigner Configuration File](../../report-server/rsreportdesigner-configuration-file.md)もします。 構成情報を削除した後は、表示拡張機能をコンポーネントに使用できません。  
  
## <a name="see-also"></a>参照  
 [Reporting Services 構成ファイル](../../report-server/reporting-services-configuration-files.md)   
 [表示拡張機能の実装](implementing-a-rendering-extension.md)   
 [表示拡張機能の概要](rendering-extensions-overview.md)   
 [IRenderingExtension インターフェイスの実装](implementing-the-irenderingextension-interface.md)   
 [拡張機能のセキュリティに関する考慮事項](../security-considerations-for-extensions.md)   
 [表示拡張機能の配置](deploying-a-rendering-extension.md)  
  
  
