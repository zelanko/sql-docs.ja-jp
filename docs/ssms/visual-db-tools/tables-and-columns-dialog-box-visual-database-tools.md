---
title: '[テーブルと列] ダイアログ ボックス (Visual Database Tools) | Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.tablesandcolumns
ms.assetid: 8cf27be1-e66d-4735-a428-9ab4b33af4f5
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 9330c2a82f2839b5fd0eb0001bdb74112653516b
ms.sourcegitcommit: 9f2edcdf958e6afce9a09fb2e572ae36dfe9edb0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/25/2018
ms.locfileid: "50099447"
---
# <a name="tables-and-columns-dialog-box-visual-database-tools"></a>[テーブルと列] ダイアログ ボックス (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
このダイアログ ボックスを使用すると、あるテーブルの主キーを別のテーブルの外部キーに割り当てることができます。 このダイアログ ボックスにアクセスするには、 **[テーブル デザイナー]** メニューの **[リレーションシップ]** をクリックします。 **[外部キーのリレーションシップ]** ダイアログ ボックスの、 **[テーブルと列の指定]** フィールドをクリックして、プロパティの右側にある省略記号 ( **[...]** ) をクリックします。  
  
> [!NOTE]  
> テーブルをレプリケーションのためにパブリッシュする場合は、Transact-SQL ステートメントの [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) または SQL Server 管理オブジェクト (SMO) を使用してスキーマを変更する必要があります。 テーブル デザイナーまたはデータベース ダイアグラム デザイナーを使用してスキーマを変更するとき、テーブルはいったん削除されてから再作成されます。 パブリッシュされたオブジェクトは削除できないので、スキーマの変更は失敗します。  
  
## <a name="options"></a>[変数]  
**[リレーションシップ名]**  
リレーションシップの名前を表示します。  
  
**[主キー テーブル]**  
データベース内のテーブルの一覧を表示します。 リレーションシップの主キー側になるテーブルを選択します。  
  
**[外部キーのテーブル]**  
リレーションシップの外部キー側のテーブルを表示します。 これは、テーブル デザイナーで現在選択されているテーブルです。  
  
**[主キー テーブル] の下のグリッド**  
**[主キー テーブル]** ボックスで選択されているテーブルの列を一覧表示します。 そのテーブルの主キーになる列を入力します。  
  
**[外部キーのテーブル] の下のグリッド**  
**[外部キーのテーブル]** ボックスで選択されているテーブルの列を一覧表示します。 主キー列に対応する外部キーのテーブルの外部キー列を入力します。  
  
> [!NOTE]  
> 外部キーに選択した列は、対応する主キー列と同じデータ型である必要があります。 各キーには同じ数の列が必要です。 たとえば、リレーションシップの主キー側になるテーブルの主キーが 2 列で構成されている場合、この各列がリレーションシップの外部キー側になるテーブルの列と一致する必要があります。  
  
## <a name="see-also"></a>参照  
[テーブル間にリレーションシップを作成する方法 (Visual Database Tools)](http://msdn.microsoft.com/867a54b8-5be4-46e6-9702-49ae6dabf67c)  
  
