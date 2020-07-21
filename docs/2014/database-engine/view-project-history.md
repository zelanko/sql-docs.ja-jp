---
title: プロジェクト履歴の表示 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- viewing project history
- version control services [SQL Server], project history
- projects [SQL Server Management Studio], historical information
- historical information [SQL Server], projects
ms.assetid: be0ea2ac-4a35-429c-9c9e-4001ea9035a4
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 1a595df602a6506f96d9f645dadecb14c5d5f4b2
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84927385"
---
# <a name="view-project-history"></a>プロジェクト履歴の表示
  [!INCLUDE[msCoName](../includes/msconame-md.md)] Visual SourceSafe (VSS) プロジェクトの履歴には、ファイルの作成、追加、削除、復元など、各プロジェクト ファイルに対して実行したすべてのアクションの一覧が記録されています。  
  
> [!NOTE]  
>  Visual SourceSafe プロジェクトは、ソース管理対象のファイルのサーバー バージョンが格納されているサーバー上の場所であり、一般にソース管理サーバー フォルダーと呼ばれています。  
  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を使用して、現在読み込まれているソリューションが属する Visual SourceSafe プロジェクトの履歴を調べることができます。 プロジェクト履歴の一部として表示されている情報に基づいて、ファイル バージョンのローカル コピーを取得したり、削除されたバージョンを復元したり、プロジェクト間でファイル バージョンを共有したりできます。  
  
### <a name="to-view-the-history-of-a-vss-project"></a>VSS プロジェクトの履歴を表示するには  
  
1.  ソリューション エクスプローラーでプロジェクトを選択します。  
  
2.  [**ファイル**] メニューの [**ソース管理**] をポイントし、[**履歴の表示**] をクリックします。  
  
3.  [**履歴** \<Project> ] ダイアログボックスで、次のいずれかの操作を実行します。  
  
    -   選択したファイルの、ソース管理システムのコピーを表示します。  
  
    -   選択したファイルに関する詳細情報を表示します。  
  
    -   選択したファイルをローカル ディスクに取得します。  
  
    -   選択したファイルをチェックアウトします。  
  
    -   2 つのソース管理プロジェクト間で、選択したファイルを共有します。  
  
    -   プリンター、ファイル、またはクリップボードに、履歴レポートをエクスポートします。  
  
## <a name="see-also"></a>参照  
 [バージョン情報の設定と取得](../../2014/database-engine/set-and-retrieve-version-information.md)   
 [ファイルの状態の表示](../../2014/database-engine/view-file-status.md)   
 [ファイルの取得](../../2014/database-engine/retrieve-files.md)   
 [ファイルの比較](../../2014/database-engine/compare-files.md)  
  
  
