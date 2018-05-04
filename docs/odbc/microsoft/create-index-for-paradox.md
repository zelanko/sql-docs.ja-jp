---
title: Paradox のインデックスを作成 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- CREATE INDEX [ODBC]
- Paradox driver [ODBC], create index
ms.assetid: 6472bd69-b931-4bc2-a9bf-f1873ed4cdfe
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8b0f8cb298dd62faee4c562943477ea0bd022a45
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="create-index-for-paradox"></a>Paradox のインデックスを作成します。
ODBC Paradox ドライバーの CREATE INDEX ステートメントの構文です。  
  
 **作成****[UNIQUE]****インデックス***インデックス名*  
  
 **ON** *テーブル名*  
  
 **(** *列識別子***[ASC]**  
  
 [**、** *列識別子***[ASC]**...**)**  
  
 ODBC Paradox ドライバー サポートしていない、 **DESC** ODBC SQL 文法を CREATE INDEX ステートメントでキーワード。 *テーブル名*引数は、テーブルの完全なパスを指定できます。  
  
 場合、キーワード**UNIQUE**を指定すると、ODBC Paradox ドライバーは、一意のインデックスを作成します。 最初の一意のインデックスは、プライマリ インデックスとして作成されます。 これは、Paradox プライマリ キーという名前のファイル*テーブル名*です。ピクセルです。 プライマリ インデックスは、次の制限が適用されます。  
  
-   任意の行がテーブルに追加される前に、プライマリ インデックスを作成する必要があります。  
  
-   プライマリ インデックスは、テーブル内の最初の"n"列に定義する必要があります。  
  
-   1 つだけのプライマリ インデックスは 1 つのテーブルで許可されています。  
  
-   プライマリ インデックスがテーブルに定義されていない場合、Paradox ドライバーによって、テーブルを更新できません。 (空のテーブル、一意のインデックスがテーブルに定義されていない場合でも更新できる場合は true ではないことに注意してください)。  
  
-   *インデックス名*プライマリ インデックスの引数には、Paradox、必要に応じて、テーブルの基本名と同じである必要があります。  
  
 場合、キーワード**UNIQUE**は省略すると、ODBC Paradox ドライバーは一意でないインデックスが作成されます。 これは、2 つの Paradox セカンダリ インデックス ファイルという名前で構成されます*テーブル名*です。X*nn*と*テーブル名*です。Y*nn*ここで、 *nn*テーブル内の列の数です。 非一意のインデックスは、次の制限が適用されます。  
  
-   テーブルの非一意のインデックスを作成することができます、前に、プライマリ インデックスがそのテーブルの存在する必要があります。  
  
-   3.*x*、*インデックス名*いずれかのインデックス (一意または一意でない)、プライマリ インデックス以外の引数には、列の名前と同じである必要があります。 4.*x*と 5 *。x*、このようなインデックスの名前が列の名前と同じである必要はありません。  
  
-   非一意のインデックスの 1 列のみを指定できます。  
  
 テーブルにインデックスを定義した後、列を追加できません。 CREATE TABLE ステートメントの引数リストの最初の列は、インデックスを作成する場合は、引数リストの 2 番目の列を含めることができません。  
  
 たとえばを使用して、販売注文番号として SO_LINES テーブルの一意のインデックス番号の列を行をステートメントを使用します。  
  
```  
CREATE UNIQUE INDEX SO_LINES  
 ON SO_LINES (SONum, LineNum)  
```  
  
 SO_LINES テーブルに非一意のインデックスとして、部品番号の列を使用するには、ステートメントを使用します。  
  
```  
CREATE INDEX PartNum  
 ON SO_LINES (PartNum)  
```  
  
 2 つの CREATE INDEX ステートメントが実行されると、最初のステートメントは常にプライマリ インデックス テーブルと同じ名前でを作成、列と同じ名前で、2 番目のステートメントで非一意のインデックスが作成されます常に注意してください。 これらのインデックスの場合でも、インデックスというラベルが付いた UNIQUE 2 番目の CREATE INDEX ステートメントと CREATE INDEX ステートメントで異なる名前が入力された場合でもこのように名前なります。  
  
> [!NOTE]  
>  Borland データベース エンジン、唯一の読み取りを実装することがなく、Paradox ドライバーを使用して追加すると、ステートメントが許可されています。
