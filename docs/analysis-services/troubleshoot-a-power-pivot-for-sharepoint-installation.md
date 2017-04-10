---
title: "Power Pivot for SharePoint インストールのトラブルシューティング | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 97bc2ce7-af04-4372-ad79-c96b8c3417ab
caps.latest.revision: 10
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 10
---
# Power Pivot for SharePoint インストールのトラブルシューティング
  予想したページや機能ではなくエラーが表示された場合は、次の操作を行います。  
  
-   SharePoint と [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] の両方のリリース ノートで、インストールの既知の問題を回避する方法を調べます。 リリース ノートは、インストール メディア、またはソフトウェアをダウンロードした Microsoft サイトで提供されています。  
  
    -   [SQL Server 2016 リリース ノート](../sql-server/sql-server-2016-release-notes.md)  
  
-   TechNet Wiki のトピック「[Power Pivot (および他のアドオン) のインストールのトラブルシューティング](http://social.technet.microsoft.com/wiki/contents/articles/13737.troubleshooting-installations-of-powerpivot-and-other-add-ins.aspx)」を参照してください。  
  
## 問題  
  
### Power Pivot ギャラリーのサムネイル画像として赤い X マークが表示される  
 考えられる原因の 1 つは、**[サイト コレクションの [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] 機能の統合]** がアクティブになっていないことです。 次の作業を完了します。  
  
1.  [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] ギャラリー ライブラリで、ギア アイコン ![SharePoint の設定](../analysis-services/media/as-sharepoint2013-settings-gear.png "SharePoint の設定") または **[ホーム]** リストのどちらかから **[サイトの設定]** をクリックします。  
  
2.  **[サイト コレクションの管理]** セクションで **[サイト コレクションの機能]** をクリックします。  
  
3.  **[サイト コレクションの機能]**をクリックします。  
  
4.  **[サイト コレクションの [!INCLUDE[ssGemini](../includes/ssgemini-md.md)] 機能の統合]** が **[アクティブ]** になっていることを確認します。  
  
 この問題に関するその他の原因については、「[Power Pivot ギャラリーでアイコンの代わりに赤い X が表示される](http://support.microsoft.com/kb/2361559)」(http://support.microsoft.com/kb/2361559) を参照してください。  
  
  