---
title: 表示拡張機能の実装 | Microsoft Docs
description: レンダリング拡張機能を実装することで、Reporting Services のレポート データとレイアウト情報をデバイス固有の形式に変換する方法について説明します。
ms.date: 03/16/2017
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: extensions
ms.topic: reference
helpviewer_keywords:
- rendering extensions [Reporting Services]
- custom rendering extensions [Reporting Services]
- transformations [Reporting Services]
- extensions [Reporting Services], rendering
- rendering extensions [Reporting Services], implementing
ms.assetid: 4a5c64f5-2391-4597-ba3f-81d265b23703
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: d61af9bd987256a2ad293f7f9566fd1a2bcd041e
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/08/2020
ms.locfileid: "84529088"
---
# <a name="implementing-a-rendering-extension"></a>表示拡張機能の実装
  表示拡張機能は、レポート サーバーのコンポーネントまたはモジュールで、レポートのデータとレイアウト情報をデバイス固有の形式に変換します。 SQL Server Reporting Services には次の 6 つの表示拡張機能があります。HTML、Excel、Word、CSV またはテキスト、XML、画像および PDF の 7 つの表示拡張機能があります。 追加の表示拡張機能を作成して、他の形式でレポートを生成できます。  
  
> [!NOTE]  
>  どの表示拡張機能を利用できるかは、RSReportServer.config ファイルのインストール済み拡張機能の一覧で確認できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [表示拡張機能の概要](../../../reporting-services/extensions/rendering-extension/rendering-extensions-overview.md)  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] のカスタム表示機能の記述方法について説明します。  
  
 [IRenderingExtension インターフェイスの実装](../../../reporting-services/extensions/rendering-extension/implementing-the-irenderingextension-interface.md)  
 表示拡張機能の属性について説明します。  
  
 [表示拡張機能の配置](../../../reporting-services/extensions/rendering-extension/deploying-a-rendering-extension.md)  
 レポート サーバーに表示拡張機能を配置する方法について説明します。  
  
 [表示拡張機能の削除](../../../reporting-services/extensions/rendering-extension/removing-a-rendering-extension.md)  
 レポート サーバーから表示拡張機能を削除する方法について説明します。  
  
## <a name="see-also"></a>参照  
 [Reporting Services の拡張機能](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Reporting Services 拡張機能ライブラリ](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  
