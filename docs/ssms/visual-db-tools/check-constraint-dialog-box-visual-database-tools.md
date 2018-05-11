---
title: '[制約のチェック] ダイアログ ボックス (Visual Database Tools) | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.component: ssms-visual-db
ms.reviewer: ''
ms.suite: sql
ms.technology: ssms
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.checkconstraint
ms.assetid: ad0bbf7f-b0de-406a-bd0a-cb779816b101
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9b72dfc8b97dfdf80e692abac8f0fc142cec5be9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="check-constraint-dialog-box-visual-database-tools"></a>[制約のチェック] ダイアログ ボックス (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
このダイアログ ボックスは、テーブル デザイナーのテーブル定義グリッドを右クリックし、 **[制約のチェック]** をクリックすると表示されます。 このダイアログ ボックスには、データベースのテーブルに関連付けられた、一意でない制約のプロパティ セットが含まれています。 UNIQUE 制約に適用されるプロパティは、 **[インデックス/キー]** ダイアログ ボックスに表示されます。  
  
> [!NOTE]  
> テーブルをレプリケーションのためにパブリッシュする場合は、Transact-SQL ステートメントの [ALTER TABLE](http://msdn.microsoft.com/en-us/f1745145-182d-4301-a334-18f799d361d1) または SQL Server 管理オブジェクト (SMO) を使用してスキーマを変更する必要があります。 テーブル デザイナーまたはデータベース ダイアグラム デザイナーを使用してスキーマを変更するとき、テーブルはいったん削除されてから再作成されます。 パブリッシュされたオブジェクトは削除できないので、スキーマの変更は失敗します。  
  
## <a name="options"></a>および  
**[選択された制約のチェック]**  
使用できる CHECK 制約を一覧表示します。 制約のプロパティを表示するには、一覧の中から選択します。  
  
**[追加]**  
選択したデータベース テーブルの制約を新しく作成し、その制約に既定の名前と他の値を割り当てます。 制約は、その制約用の式を入力するまで、有効にできません。  
  
**削除**  
選択した制約をテーブルから削除します。 追加した CHECK 制約を取り消すには、このボタンを使用して制約を削除します。  
  
**[全般] カテゴリ**  
展開して **[式]** のプロパティ フィールドを表示します。  
  
**[式]**  
選択した CHECK 制約の式を表示します。 新しい制約の場合は、このボックスを終了する前に式を入力する必要があります。 既存の CHECK 制約を編集することもできます。 詳細については、「 [制約の使用 (Visual Database Tools)](http://msdn.microsoft.com/en-us/637098af-2567-48f8-90f4-b41df059833e)」を参照してください。  
  
**[IDENTITY] カテゴリ**  
展開して **[名前]** と **[説明]** のプロパティを表示します。  
  
**[名前]**  
選択した CHECK 制約の名前を表示します。 この制約の名前を変更するには、プロパティ フィールドに直接テキストを入力します。  
  
**[説明]**  
この CHECK 制約の説明を記述します。 プロパティ フィールドに入力することで説明を編集できます。またプロパティ フィールドの右側に表示されている省略記号ボタン (**[...]**) をクリックすると、 **[説明のプロパティ]** ダイアログ ボックスで説明を編集できます。  
  
**[テーブル デザイナー] カテゴリ**  
展開して **[作成時または再度有効化するときに既存データを確認]**、 **[INSERTs および UPDATEs に適用]**、および **[レプリケーションに対して適用]** の各プロパティを表示します。  
  
**Check Existing Data On Creation or Re-Enabling**  
既存のすべてのデータ (制約を作成する前からテーブルに存在しているデータ) を制約で検証するかどうかを指定します。  
  
**[INSERTs および UPDATEs に適用]**  
テーブルにデータを挿入するときやテーブルのデータを更新するときに、制約を適用するかどうかを指定します。  
  
**[レプリケーションに対して適用]**  
レプリケーション エージェントがこのテーブルに対して挿入または更新を行うときに制約を適用するかどうかを示します。  
  
## <a name="see-also"></a>参照  
[制約の使用 (Visual Database Tools)](http://msdn.microsoft.com/en-us/637098af-2567-48f8-90f4-b41df059833e)  
[[インデックス/キー] ダイアログ ボックス (Visual Database Tools)](../../ssms/visual-db-tools/indexes-keys-dialog-box-visual-database-tools.md)  
  
