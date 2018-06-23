---
title: PowerPivot for SharePoint のインストールのトラブルシューティングを行う |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 97bc2ce7-af04-4372-ad79-c96b8c3417ab
caps.latest.revision: 6
author: markingmyname
ms.author: maghan
manager: jhubbard
ms.openlocfilehash: b4881ce3be8ede7d97dc2b71fb464b94b8677ca0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085353"
---
# <a name="troubleshoot-a-powerpivot-for-sharepoint-installation"></a>PowerPivot for SharePoint インストールのトラブルシューティング
  予想したページや機能ではなくエラーが表示された場合は、次の操作を行います。  
  
-   SharePoint と [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の両方のリリース ノートで、インストールの既知の問題を回避する方法を調べます。 リリース ノートは、インストール メディア、またはソフトウェアをダウンロードした Microsoft サイトで提供されています。  
  
    -   [SQL Server 2014 リリース ノート](http://technet.microsoft.com/library/dn169381\(v=sql.15\).aspx).  
  
-   Technet wiki のトピックを参照してください[PowerPivot のインストールのトラブルシューティング (およびその他のアドイン)](http://social.technet.microsoft.com/wiki/contents/articles/13737.troubleshooting-installations-of-powerpivot-and-other-add-ins.aspx)です。  
  
## <a name="issues"></a>問題  
  
### <a name="powerpivot-gallery-thumbnail-images-show-as-a-red-x"></a>PowerPivot ギャラリーのサムネイル画像として赤い X マークが表示される  
 1 つの考えられる原因は、 **PowerPivot 機能統合サイト コレクションを**アクティブではありません。 次の作業を完了します。  
  
1.  PowerPivot ギャラリー ライブラリ をクリックして**サイト設定**歯車アイコンから![SharePoint 設定](../../../2014/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint 設定")または**ホーム**  ボックスの一覧です。  
  
2.  **[サイト コレクションの管理]** セクションで **[サイト コレクションの機能]** をクリックします。  
  
3.  **[サイト コレクションの機能]** をクリックします。  
  
4.  確認**PowerPivot 機能統合サイト コレクションを**は**Active**です。  
  
 この問題の原因を追加を参照してください。 [PowerPivot ギャラリーでアイコンの赤い x 印](http://support.microsoft.com/kb/2361559)(http://support.microsoft.com/kb/2361559)です。  
  
  