---
title: データベース ダイアグラム間でのテーブルのコピー
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- copying tables
- duplicating tables
ms.assetid: 155a4f09-9321-4887-a7d4-aa2ce6b51277
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.openlocfilehash: 887cc2cdb2d70b0d69599d75d8534907552cb201
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/29/2020
ms.locfileid: "75254390"
---
# <a name="copy-tables-from-one-database-diagrams-to-another-visual-database-tools"></a>データベース ダイアグラム間でのテーブルのコピー (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
データベース ダイアグラムから同じデータベースの他のデータベース ダイアグラムにテーブルをコピーできます。  
  
データベース ダイアグラム間でテーブルをコピーすると、コピー先のダイアグラムのテーブルに参照が追加されます。 テーブルがデータベースに複製されるわけではありません。 たとえば、データベース ダイアグラム間で `authors` テーブルをコピーすると、各ダイアグラムはデータベースの同じ `authors` テーブルを参照します。  
  
### <a name="to-copy-a-table-from-another-database-diagram"></a>他のデータベース ダイアグラムからテーブルをコピーするには  
  
1.  テーブルをコピーするデータベースに接続していることを確認します。  
  
2.  コピー元およびコピー先のデータベース ダイアグラムを開き、コピー元のダイアグラムで、コピー先のダイアグラムにコピーするテーブルを選択します。  
  
3.  ツール バーの **[コピー]** ボタンをクリックします。 選択したテーブルの定義がクリップボードにコピーされます。  
  
4.  コピー先のダイアグラムに切り替えます。 このダイアグラムは、コピー元のダイアグラムと同じデータベースにある必要があります。  
  
5.  ツール バーの **[貼り付け]** ボタンをクリックします。 クリップボードの内容が新しい場所に表示され、他の場所をクリックするまで強調表示された状態が続きます。 コピー先のダイアグラムで、選択したテーブルとダイアグラムの他のテーブルとの間にリレーションシップが存在する場合は、自動的にリレーションシップの線が引かれます。  
  
どちらかのダイアグラムでテーブルを編集すると、両方のダイアグラムに変更が反映されます。 同様に、どちらかのダイアグラムのテーブルを保存すると、どちらのダイアグラムでもテーブルは "変更済み" と見なされなくなります。  
  
## <a name="see-also"></a>参照  
[データベース ダイアグラムの使用 (Visual Database Tools)](../../ssms/visual-db-tools/work-with-database-diagrams-visual-database-tools.md)  
[ダイアグラムへのテーブルの追加 (Visual Database Tools)](../../ssms/visual-db-tools/add-tables-to-diagrams-visual-database-tools.md)  
  
