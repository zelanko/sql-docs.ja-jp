---
title: 表示拡張機能の削除 | Microsoft Docs
ms.date: 03/18/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- deleting rendering extensions
- removing rendering extensions
- rendering extensions [Reporting Services], removing
ms.assetid: 2abfebfb-065f-45cc-a904-c914394cf900
author: markingmyname
ms.author: maghan
ms.openlocfilehash: bd360d5a4929ab41c7b77e60b59b394f127f6f13
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47723880"
---
# <a name="removing-a-rendering-extension"></a>表示拡張機能の削除
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 表示拡張機能を削除する場合は、**%ProgramFiles%\Microsoft SQL Server\MSRS10_50.\<インスタンス名>\Reporting Services\ReportServer** フォルダーにある、rsreportserver.config ファイルから表示拡張機能の **Extension** 要素を削除するだけです。 レポート サーバーに加えてレポート デザイナーにもエントリを作成した場合は、[RSReportDesigner 構成ファイル](../../../reporting-services/report-server/rsreportdesigner-configuration-file.md)からも **Extension** 要素を削除します。 構成情報を削除した後は、表示拡張機能をコンポーネントに使用できません。  
  
## <a name="see-also"></a>参照  
 [Reporting Services 構成ファイル](../../../reporting-services/report-server/reporting-services-configuration-files.md)   
 [表示拡張機能の実装](../../../reporting-services/extensions/rendering-extension/implementing-a-rendering-extension.md)   
 [表示拡張機能の概要](../../../reporting-services/extensions/rendering-extension/rendering-extensions-overview.md)   
 [IRenderingExtension インターフェイスの実装](../../../reporting-services/extensions/rendering-extension/implementing-the-irenderingextension-interface.md)   
 [拡張機能のセキュリティに関する考慮事項](../../../reporting-services/extensions/security-considerations-for-extensions.md)   
 [表示拡張機能の配置](../../../reporting-services/extensions/rendering-extension/deploying-a-rendering-extension.md)  
  
  
