---
title: 表示拡張機能の削除 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- deleting rendering extensions
- removing rendering extensions
- rendering extensions [Reporting Services], removing
ms.assetid: 2abfebfb-065f-45cc-a904-c914394cf900
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 77a8a9ac44b35f338f978913985617e4f264ddb7
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62988058"
---
# <a name="removing-a-rendering-extension"></a>表示拡張機能の削除
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]表示拡張機能を削除するには、 `Extension` **%ProgramFiles%\Microsoft SQL Server \ MSRS10_50 にある rsreportserver. .config ファイルから表示拡張機能の要素を削除する\<だけです。インスタンス名> \ Reporting Services\ReportServer**フォルダー。 レポートサーバーだけでなくレポートデザイナーのエントリを作成した場合は、 `Extension` [Rsreportdesigner 構成ファイル](../../report-server/rsreportdesigner-configuration-file.md)からも要素を削除します。 構成情報を削除した後は、表示拡張機能をコンポーネントに使用できません。  
  
## <a name="see-also"></a>参照  
 [Reporting Services 構成ファイル](../../report-server/reporting-services-configuration-files.md)   
 [表示拡張機能の実装](implementing-a-rendering-extension.md)   
 [表示拡張機能の概要](rendering-extensions-overview.md)   
 [IRenderingExtension インターフェイスの実装](implementing-the-irenderingextension-interface.md)   
 [拡張機能のセキュリティに関する考慮事項](../security-considerations-for-extensions.md)   
 [表示拡張機能の配置](deploying-a-rendering-extension.md)  
  
  
