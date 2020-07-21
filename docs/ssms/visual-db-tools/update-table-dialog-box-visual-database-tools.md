---
title: '[テーブルの更新] ダイアログ ボックス'
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- vdt.dlgbox.updatetable
- vdtsql.chm:69643
ms.assetid: 174c7275-5b15-42a9-b172-5ff30de575a1
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.openlocfilehash: 5af6b442486a1c80a1b9ec9f8d870f167c67de35
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "75246038"
---
# <a name="update-table-dialog-box-visual-database-tools"></a>[テーブルの更新] ダイアログ ボックス (Visual Database Tools)

[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

このダイアログ ボックスを使用すると、更新するテーブルを指定できます。

クエリの種類を UPDATE クエリに変更するときに、ダイアグラム ペインに複数のテーブルが表示される場合、このダイアログ ボックスが表示されます。  

更新するテーブルを選択し、 **[OK]** をクリックします。

> [!NOTE]
> テーブルをレプリケーションのためにパブリッシュする場合は、Transact-SQL ステートメントの [ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md) または SQL Server 管理オブジェクト (SMO) を使用してスキーマを変更する必要があります。 テーブル デザイナーまたはデータベース ダイアグラム デザイナーを使用してスキーマを変更するとき、テーブルはいったん削除されてから再作成されます。 パブリッシュされたオブジェクトは削除できないので、スキーマの変更は失敗します。

## <a name="see-also"></a>参照

[更新クエリの作成](../../ssms/visual-db-tools/create-update-queries-visual-database-tools.md)