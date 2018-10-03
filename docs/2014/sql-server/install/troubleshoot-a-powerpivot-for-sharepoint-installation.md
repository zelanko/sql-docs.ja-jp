---
title: PowerPivot for SharePoint のインストールのトラブルシューティングを行う |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
ms.assetid: 97bc2ce7-af04-4372-ad79-c96b8c3417ab
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: a80e3134fc734f962fa9b082374dc3f9c4a74ba2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48147252"
---
# <a name="troubleshoot-a-powerpivot-for-sharepoint-installation"></a>PowerPivot for SharePoint インストールのトラブルシューティング
  予想したページや機能ではなくエラーが表示された場合は、次の操作を行います。  
  
-   SharePoint と [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の両方のリリース ノートで、インストールの既知の問題を回避する方法を調べます。 リリース ノートは、インストール メディア、またはソフトウェアをダウンロードした Microsoft サイトで提供されています。  
  
    -   [SQL Server 2014 リリース ノート](http://technet.microsoft.com/library/dn169381\(v=sql.15\).aspx).  
  
-   Technet wiki のトピックを参照してください。 [PowerPivot のインストールのトラブルシューティング (およびその他のアドイン)](http://social.technet.microsoft.com/wiki/contents/articles/13737.troubleshooting-installations-of-powerpivot-and-other-add-ins.aspx)します。  
  
## <a name="issues"></a>問題  
  
### <a name="powerpivot-gallery-thumbnail-images-show-as-a-red-x"></a>PowerPivot ギャラリーのサムネイル画像として赤い X マークが表示される  
 1 つの考えられる原因は、 **PowerPivot 機能の統合サイト コレクション**アクティブではありません。 次の作業を完了します。  
  
1.  PowerPivot ギャラリー ライブラリでクリックして**サイト設定**歯車アイコンから![SharePoint 設定](../../../2014/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint 設定")または**ホーム**一覧。  
  
2.  **[サイト コレクションの管理]** セクションで **[サイト コレクションの機能]** をクリックします。  
  
3.  **[サイト コレクションの機能]** をクリックします。  
  
4.  確認**PowerPivot 機能の統合サイト コレクション**は**Active**します。  
  
 この問題の原因を追加を参照してください。 [PowerPivot ギャラリーには、代わりのアイコンに赤い x が表示されます。](http://support.microsoft.com/kb/2361559) (http://support.microsoft.com/kb/2361559)します。  
  
  
