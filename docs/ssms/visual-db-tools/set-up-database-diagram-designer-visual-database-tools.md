---
title: "データベース ダイアグラム デザイナーの設定 (Visual Database Tools) | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: sql-tools
ms.service: 
ms.component: ssms-visual-db
ms.reviewer: 
ms.suite: sql
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vdt.diagnostic.InstallSqlDiagramSupport
helpviewer_keywords:
- Database Diagram Designer
- database diagrams [SQL Server], Database Diagram Designer
- diagrams [SQL Server], Database Diagram Designer
ms.assetid: 927321ee-b459-4f5b-9719-4a7a95639143
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: e7fa34af156764f2780a479069fa2919ec2ea103
ms.sourcegitcommit: b6116b434d737d661c09b78d0f798c652cf149f3
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/17/2018
---
# <a name="set-up-database-diagram-designer-visual-database-tools"></a>データベース ダイアグラム デザイナーの設定 (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)] データベース ダイアグラム デザイナーを使用するには、**db_owner** ロールのメンバーによって、ダイアグラムへのアクセスを制御するようにあらかじめ設定しておく必要があります。  
  
### <a name="to-set-up-database-diagramming"></a>データベース ダイアグラムを設定するには  
  
1.  オブジェクト エクスプローラーから、データベース ノードを展開します。  
  
2.  データベース接続のデータベース ダイアグラム ノードを展開します。  
  
3.  データベースのダイアグラム化を設定するかどうかをたずねるメッセージが表示されたら、 **[はい]** を選択します。  
  
    > [!NOTE]  
    > これにより、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] データベースにデータベース ダイアグラム テーブル、システム ストアド プロシージャ、およびシステム関数が作成されます。  
  
4.  Visual Studio では、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]のインスタンスに次のオブジェクトが作成されます。  
  
    1.  sysdiagrams テーブル  
  
    2.  sp_alterdiagram ストアド プロシージャ  
  
    3.  sp_creatediagram ストアド プロシージャ  
  
    4.  sp_dropdiagram ストアド プロシージャ  
  
    5.  sp_renamediagram ストアド プロシージャ  
  
    6.  fn_diagramobjects 関数  
  
    7.  sp_helpdiagrams ストアド プロシージャ  
  
    8.  sp_helpdiagramsdefinition ストアド プロシージャ  
  
    9. sp_upgraddiagrams ストアド プロシージャ  
  
## <a name="see-also"></a>参照  
[データベース ダイアグラムの所有権について (Visual Database Tools)](../../ssms/visual-db-tools/understand-database-diagram-ownership-visual-database-tools.md)  
[旧エディションのデータベース ダイアグラムのアップグレード (Visual Database Tools)](../../ssms/visual-db-tools/upgrade-database-diagrams-from-previous-editions-visual-database-tools.md)  
[ALTER AUTHORIZATION (Transact-SQL)](http://msdn.microsoft.com/en-us/8c805ae2-91ed-4133-96f6-9835c908f373)  
  
