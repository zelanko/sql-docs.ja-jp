---
title: パラドックスのインデックスを作成する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- CREATE INDEX [ODBC]
- Paradox driver [ODBC], create index
ms.assetid: 6472bd69-b931-4bc2-a9bf-f1873ed4cdfe
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2e68484efdc5194f93f2acab31973377d9c66f1c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280912"
---
# <a name="create-index-for-paradox"></a>Paradox の CREATE INDEX
ODBC パラドックス ドライバーの CREATE INDEX ステートメントの構文は次のとおりです。  
  
 **作成**[**UNIQUE**]**インデックス***インデックス名*  
  
 **オン***テーブル名*  
  
 **(** *カラム識別子*[**ASC**]  
  
 [**,** *列識別子*[**ASC.]****)**  
  
 ODBC パラドックス ドライバーは、CREATE INDEX ステートメントの ODBC SQL 文法で**DESC**キーワードをサポートしていません。 *table-name*引数には、テーブルの完全パスを指定できます。  
  
 キーワード**UNIQUE**を指定すると、ODBC Paradox ドライバは一意のインデックスを作成します。 最初の一意インデックスは、プライマリ インデックスとして作成されます。 これは *、table-name*という名前の Paradox の主キー ファイルです。ピクセル。 プライマリ インデックスには、次の制限があります。  
  
-   行をテーブルに追加する前に、プライマリ インデックスを作成する必要があります。  
  
-   主インデックスは、テーブルの最初の "n" 列に定義する必要があります。  
  
-   テーブルごとに 1 つのプライマリ インデックスのみ使用できます。  
  
-   テーブルにプライマリ インデックスが定義されていない場合、Paradox ドライバによってテーブルを更新することはできません。 (これは、表に一意索引が定義されていない場合でも更新できる空の表には当てはまらないことに注意してください。  
  
-   1 次索引*の index-name*引数は、Paradox の要求に応じて、テーブルのベース名と同じでなければなりません。  
  
 キーワード**UNIQUE**を省略すると、ODBC Paradox ドライバは一意でないインデックスを作成します。 このファイルは *、 table-name*という 2 つの Paradox セカンダリ インデックス ファイルで構成されます。X*nn*と*テーブル名*。Y*nn*、 *nn*はテーブル内の列の番号です。 非ユニーク索引には、以下の制約があります。  
  
-   テーブルに対して非ユニーク索引を作成するには、その表に対して 1 次索引が存在している必要があります。  
  
-   パラドックス3の場合。*x*の場合、1 次索引以外の索引 (固有または非固有) の*index-name*引数は、列名と同じでなければなりません。 パラドックス4の場合。*x*および 5.*x*を指定すると、このようなインデックスの名前は列名と同じである必要はありませんが、その名前にする必要はありません。  
  
-   一意でないインデックスには、1 つの列のみ指定できます。  
  
 テーブルにインデックスを定義した後は、列を追加できません。 CREATE TABLE ステートメントの引数リストの最初の列が索引を作成する場合、2 番目の列を引数リストに含めることはできません。  
  
 たとえば、販売注文番号と行番号の列をSO_LINESテーブルの一意のインデックスとして使用するには、次のステートメントを使用します。  
  
```  
CREATE UNIQUE INDEX SO_LINES  
 ON SO_LINES (SONum, LineNum)  
```  
  
 SO_LINESテーブルの非一意インデックスとして部品番号列を使用するには、次のステートメントを使用します。  
  
```  
CREATE INDEX PartNum  
 ON SO_LINES (PartNum)  
```  
  
 CREATE INDEX ステートメントが 2 つ実行されると、最初のステートメントは常にテーブルと同じ名前のプライマリ インデックスを作成し、2 番目のステートメントは常に列と同じ名前の非ユニークインデックスを作成します。 これらの索引は、CREATE INDEX ステートメントに異なる名前が入力されていても、その索引が 2 番目の CREATE INDEX ステートメントで UNIQUE というラベルが付いている場合でも、このように命名されます。  
  
> [!NOTE]  
>  ボーランド データベース エンジンを実装せずに Paradox ドライバを使用する場合、読み取りステートメントと追加ステートメントのみが許可されます。
