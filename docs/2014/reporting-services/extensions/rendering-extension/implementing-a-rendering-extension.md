---
title: 表示拡張機能の実装 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- rendering extensions [Reporting Services]
- custom rendering extensions [Reporting Services]
- transformations [Reporting Services]
- extensions [Reporting Services], rendering
- rendering extensions [Reporting Services], implementing
ms.assetid: 4a5c64f5-2391-4597-ba3f-81d265b23703
caps.latest.revision: 33
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: 531880091bfd540fb42a84d63099d2e5006b2e36
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37210872"
---
# <a name="implementing-a-rendering-extension"></a>表示拡張機能の実装
  表示拡張機能は、レポート サーバーのコンポーネントまたはモジュールで、レポートのデータとレイアウト情報をデバイス固有の形式に変換します。 SQL Server Reporting Services には 6 種類の表示拡張機能 (HTML、Excel、Word、CSV (Text)、XML、Image、PDF) があります。 追加の表示拡張機能を作成して、他の形式でレポートを生成できます。  
  
> [!NOTE]  
>  どの表示拡張機能を利用できるかは、RSReportServer.config ファイルのインストール済み拡張機能の一覧で確認できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [表示拡張機能の概要](rendering-extensions-overview.md)  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のカスタム表示機能の記述方法について説明します。  
  
 [IRenderingExtension インターフェイスの実装](implementing-the-irenderingextension-interface.md)  
 表示拡張機能の属性について説明します。  
  
 [表示拡張機能の配置](deploying-a-rendering-extension.md)  
 レポート サーバーに表示拡張機能を配置する方法について説明します。  
  
 [表示拡張機能の削除](removing-a-rendering-extension.md)  
 レポート サーバーから表示拡張機能を削除する方法について説明します。  
  
## <a name="see-also"></a>参照  
 [Reporting Services の拡張機能](../reporting-services-extensions.md)   
 [Reporting Services 拡張機能ライブラリ](../reporting-services-extension-library.md)  
  
  
