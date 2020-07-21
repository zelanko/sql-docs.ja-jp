---
title: PowerPivot for SharePoint のインストールのトラブルシューティング |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 97bc2ce7-af04-4372-ad79-c96b8c3417ab
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: e078becc9267c84fe139a151a15f9f67050161a8
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85035846"
---
# <a name="troubleshoot-a-powerpivot-for-sharepoint-installation"></a>PowerPivot for SharePoint インストールのトラブルシューティング
  予想したページや機能ではなくエラーが表示された場合は、次の操作を行います。  
  
-   SharePoint と [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の両方のリリース ノートで、インストールの既知の問題を回避する方法を調べます。 リリース ノートは、インストール メディア、またはソフトウェアをダウンロードした Microsoft サイトで提供されています。  
  
    -   [SQL Server 2014 リリースノート](https://technet.microsoft.com/library/dn169381\(v=sql.15\).aspx)。  
  
-   Technet wiki トピック「 [PowerPivot (およびその他のアドイン) のインストールのトラブルシューティング](https://social.technet.microsoft.com/wiki/contents/articles/13737.troubleshooting-installations-of-powerpivot-and-other-add-ins.aspx)」を参照してください。  
  
## <a name="issues"></a>発行  
  
### <a name="powerpivot-gallery-thumbnail-images-show-as-a-red-x"></a>PowerPivot ギャラリーのサムネイル画像として赤い X マークが表示される  
 考えられる原因の1つは、**サイトコレクションの PowerPivot 機能の統合**がアクティブではないことです。 次の作業を完了します。  
  
1.  PowerPivot ギャラリーライブラリで、歯車アイコン![SharePoint の設定](https://docs.microsoft.com/analysis-services/analysis-services/media/as-sharepoint2013-settings-gear.gif "SharePoint の設定")または**ホーム**リストから [サイトの**設定**] をクリックします。  
  
2.  **[サイト コレクションの管理]** セクションで **[サイト コレクションの機能]** をクリックします。  
  
3.  **[サイト コレクションの機能]** をクリックします。  
  
4.  **サイトコレクションの PowerPivot 機能の統合**が**アクティブ**であることを確認します。  
  
 この問題のその他の原因については、「 [PowerPivot ギャラリーのアイコン](https://support.microsoft.com/kb/2361559)()」を参照してください https://support.microsoft.com/kb/2361559) 。  
  
  
