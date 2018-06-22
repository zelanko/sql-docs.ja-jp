---
title: UNIQUE 制約の変更 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- modifying constraints
- UNIQUE constraints [SQL Server], modifying
- constraints [SQL Server], modifying
- constraints [SQL Server], unique
ms.assetid: fddbdc9e-958b-4614-8e88-6ca205d64a4e
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 2f0898fdbc52d964834f39f6365f0a74efd97728
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36083614"
---
# <a name="modify-unique-constraints"></a>UNIQUE 制約の変更
  [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] では、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] または [!INCLUDE[tsql](../../includes/tsql-md.md)]を使用して UNIQUE 制約を変更できます。  
  
 **このトピックの内容**  
  
-   **作業を開始する準備:**  
  
     [Security](#Security)  
  
-   **UNIQUE 制約を変更するための方法:**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> 作業を開始する準備  
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 テーブルに対する ALTER 権限が必要です。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-modify-a-unique-constraint"></a>UNIQUE 制約を変更するには  
  
1.  **オブジェクト エクスプローラー**で、UNIQUE 制約を含むテーブルを右クリックし、 **[デザイン]** をクリックします。  
  
2.  **[テーブル デザイナー]** メニューの **[インデックス/キー…]** をクリックします。  
  
3.  **[インデックス/キー]** ダイアログ ボックスの **[選択された主/一意キーまたはインデックス]** で、編集する制約を選択します。  
  
4.  次の表の操作を完了します。  
  
    |変換先|手順|  
    |--------|------------------------|  
    |制約を適用する列を変更する。|1) **[(全般)]** の下のグリッドで、 **[列]** をクリックし、プロパティの右にある省略記号 ( **[...]** ) をクリックします。<br /><br /> 2) **[インデックス列]** ダイアログ ボックスで、インデックスの新しい列または並べ替え順序、あるいはその両方を指定します。|  
    |制約名を変更する。|**[ID]** の下のグリッドで、 **[名前]** ボックスに新しい名前を入力します。 新しい名前が **[選択された主/一意キーまたはインデックス]** ボックスの一覧の名前と重複していないことを確認します。|  
    |クラスター化オプションを設定する。|**[テーブル デザイナー]** の下のグリッドで、 **[CLUSTERED として作成]** をクリックします。クラスター化インデックスを作成するには、ドロップダウン メニューの [はい] をクリックし、非クラスター化インデックスを作成する場合は [いいえ] をクリックします。 1 つのテーブルには、クラスター化インデックスを 1 つだけ作成できます。 このテーブルにクラスター化インデックスが既に存在する場合は、元のインデックスに対してこの設定をオフにする必要があります。|  
    |FILL FACTOR を定義する。|**[テーブル デザイナー]** の下のグリッドで、 **[FILL の指定]** カテゴリを展開し、 **[FILL FACTOR]** ボックスに 0 ～ 100 の整数を入力します。|  
  
5.  **[ファイル]** メニューの *[<テーブル名> を保存]* をクリックします。  
  
##  <a name="TsqlProcedure"></a> **UNIQUE 制約を変更するには**  
  
 Transact-SQL を使用して UNIQUE 制約を変更するには、まず既存の UNIQUE 制約を削除してから、新しい定義を使用して再作成する必要があります。 詳細については、「 [Delete Unique Constraints](delete-unique-constraints.md) 」および「 [Create Unique Constraints](create-unique-constraints.md)」を参照してください。  
  
###  <a name="TsqlExample"></a>  