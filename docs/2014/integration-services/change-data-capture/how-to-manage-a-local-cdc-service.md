---
title: ローカルの CDC Service を管理する方法 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 7f9be649-cd93-40c1-bc48-0480106f207c
caps.latest.revision: 5
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 1d913d41b9a94e0dbc407b64f23c382bdbded6c1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37187179"
---
# <a name="how-to-manage-a-local-cdc-service"></a>ローカルの CDC Service を管理する方法
  この手順では、CDC Service 構成コンソールを使用して特定の CDC サービスを管理する方法について説明します。  
  
### <a name="to-manage-a-specific-cdc-service"></a>特定の CDC Service を管理するには  
  
1.  **[スタート]** メニューの **[CDC Service Configuration for Oracle]** をクリックします。  
  
2.  CDC Service 構成コンソールの左ペインで **[ローカルの CDC Service]** を展開します。  
  
3.  操作する CDC サービスを選択します。  
  
     操作する CDC サービスを右クリックして、目的のアクションをクリックすることもできます。  
  
     **または**  
  
     CDC Service 構成コンソールの左ペインで **[ローカルの CDC Service]** をクリックし、作業するサービスを CDC Service 構成コンソールの中央のセクションで選択します。  
  
     操作する CDC サービスを右クリックして、目的のアクションをクリックすることもできます。  
  
4.  CDC サービスの操作時には、以下のタスクを実行できます。  
  
    -   **サービスの削除**  
  
         サービスを削除するには、CDC Service 構成コンソールの右側にある **[アクション]** ペインで **[削除]** をクリックします。  
  
         または、削除する CDC サービスを右クリックして **[削除]** を選択します。  
  
         **注**: 実行中のサービスを削除した場合、サービスは停止されてから削除されます。  
  
         Oracle CDC Windows Service の定義を削除するには、プログラムに、関連付けられている [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス内の MSXDBCDC データベースに対する更新アクセスが必要です。 **[OK]** をクリックしてサービスを削除すると、MSXDBCDC データベース内にある Oracle CDC Service 登録の削除が試みられます。 権限がないために削除できない場合、MSXDBCDC データベースに対する更新アクセスを持つ [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインを入力するためのダイアログ ボックスが表示されます。  
  
         [SQL Server への接続] ダイアログ ボックスに入力するデータについては、「 [Manage an Oracle CDC Service](manage-an-oracle-cdc-service.md) 」および「 [Connection to SQL Server for Delete](connection-to-sql-server-for-delete.md)」を参照してください。  
  
    -   **CDC Service のプロパティの編集**  
  
         CDC Service 構成コンソールの右側にある **[アクション]** ペインで **[プロパティ]** をクリックします。  
  
         または、プロパティを編集する CDC サービスを右クリックして **[プロパティ]** を選択します。  
  
## <a name="see-also"></a>参照  
 [Oracle CDC Service の管理](manage-an-oracle-cdc-service.md)  
  
  
