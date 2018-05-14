---
title: プロジェクトへの新規項目の追加 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-solutions
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- projects [SQL Server Management Studio], item additions
- adding project items
ms.assetid: 76af8692-324f-4f5e-b1a0-d72ca8a107e3
caps.latest.revision: 4
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 01a3d385d52f90eb48cf9c4ca6f9b19c9639e596
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="add-new-items-to-a-project"></a>プロジェクトへの新規項目の追加
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
プロジェクトに新しい項目を追加して、アプリケーションの機能を拡張できます。 新しい項目にできるのは、クエリまたは接続です。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] スクリプト プロジェクトおよび Analysis Services スクリプト プロジェクトという 2 種類のプロジェクトがあります。 プロジェクトの種類によって、プロジェクトに追加できるアイテムが決まります。 たとえば、 [!INCLUDE[tsql](../../includes/tsql_md.md)] クエリ (拡張子が .sql のファイル) は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] スクリプト プロジェクトには追加できますが、Analysis Services スクリプト プロジェクトには追加できません。  
  
[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] では、プロジェクト内にフォルダーを作成することはできません。 作業を整理するには、ソリューション内に複数のプロジェクトを作成してください。  
  
### <a name="to-add-a-new-query-to-an-existing-project"></a>既存のプロジェクトに新しいクエリを追加するには  
  
1.  ソリューション エクスプローラーで、対象のプロジェクトを選択します。  
  
2.  **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。  
  
3.  **[新しい項目の追加]** ダイアログ ボックスの左側のペインで、カテゴリを選択します。  
  
4.  右側のペインでクエリ テンプレートを選択し、 **[追加]** をクリックします。 新しいクエリがプロジェクトの **[クエリ]** フォルダーに追加されます。  
  
5.  **[データベース エンジンへの接続]** ダイアログ ボックスで、新しいクエリの接続を指定し、 **[接続]** をクリックします。 新しいクエリに接続を関連付けたくない場合は、接続ダイアログの **[キャンセル]** をクリックすることもできます。  
  
6.  必要に応じて、ソリューション エクスプローラーでクエリの名前を変更します。  
  
### <a name="to-add-a-new-connection-to-an-existing-project"></a>既存のプロジェクトに新しい接続を追加するには  
  
1.  ソリューション エクスプローラーで、対象のプロジェクトを選択します。  
  
2.  **[プロジェクト]** メニューの **[新しい項目の追加]** をクリックします。  
  
3.  左ペインで **[接続]** を選択します。  
  
4.  右側のペインで **[新しい接続]** を選択し、 **[追加]** をクリックします。  
  
5.  **[データベース エンジンへの接続]** ダイアログ ボックスで、新しいクエリの接続を指定し、 **[接続]** をクリックします。 新しい接続がプロジェクトの **[接続]** フォルダーに追加されます。  
  
## <a name="see-also"></a>参照  
[ソリューション エクスプローラー](../../ssms/solution/solution-explorer.md)  
[ファイル拡張子をコード エディターに関連付ける](http://msdn.microsoft.com/en-us/193630f4-93de-4950-8f36-68702531f925)  
[既存の項目をプロジェクトに追加する](../../ssms/solution/add-existing-items-to-a-project.md)  
[アイテムやプロジェクトのクリアまたは削除](../../ssms/solution/remove-or-delete-an-item-or-project.md)  
  
