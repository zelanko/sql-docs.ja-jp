---
title: Paradox の CREATE INDEX |Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 331613676b748453a56da1e41fe85f04a7715038
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68081938"
---
# <a name="create-index-for-paradox"></a>Paradox の CREATE INDEX
ODBC Paradox ドライバーの CREATE INDEX ステートメントの構文は次のとおりです。  
  
 **CREATE** [**UNIQUE**]**インデックス***のインデックス名*  
  
 **** *テーブル名*  
  
 **(** *列識別子*[**ASC**]  
  
 [**,** *列識別子*[**ASC**]...]**)**  
  
 ODBC Paradox ドライバーでは、CREATE INDEX ステートメントの ODBC SQL 文法で**DESC**キーワードがサポートされていません。 *テーブル名*引数には、テーブルの完全なパスを指定できます。  
  
 キーワード**unique**が指定されている場合は、ODBC Paradox ドライバーによって一意のインデックスが作成されます。 最初の一意インデックスは、プライマリインデックスとして作成されます。 これは、*テーブル名*という名前の Paradox プライマリキーファイルです。ピクセル. プライマリインデックスには、次の制限が適用されます。  
  
-   テーブルに行を追加する前に、プライマリインデックスを作成する必要があります。  
  
-   プライマリインデックスは、テーブルの最初の "n" 列に対して定義する必要があります。  
  
-   テーブルごとに1つのプライマリインデックスのみが許可されます。  
  
-   テーブルでプライマリインデックスが定義されていない場合、Paradox ドライバーでテーブルを更新することはできません。 (テーブルで一意のインデックスが定義されていない場合でも更新できる空のテーブルについては、これは当てはまりません)。  
  
-   プライマリインデックスの*インデックス名*引数は、Paradox の必要に応じて、テーブルのベース名と同じである必要があります。  
  
 キーワード**unique**が省略されている場合、ODBC Paradox ドライバーは一意でないインデックスを作成します。 これは *、テーブル名*という名前の2つの Paradox セカンダリインデックスファイルで構成されます。X*nn*と*テーブル名*。Y*nn*。ここで、 *nn*はテーブル内の列の番号です。 一意でないインデックスには、次の制限が適用されます。  
  
-   テーブルに対して一意でないインデックスを作成する前に、そのテーブルのプライマリインデックスが存在している必要があります。  
  
-   Paradox 3 の場合。*x*では、プライマリインデックス以外のインデックス (一意または非一意) のインデックス*名*引数は、列名と同じである必要があります。 Paradox 4 の場合。*x*および5。*x*の場合、このようなインデックスの名前は、列名と同じにすることができますが、同じである必要はありません。  
  
-   一意でないインデックスに対して指定できる列は1つだけです。  
  
 テーブルでインデックスが定義された後は、列を追加することはできません。 CREATE TABLE ステートメントの引数リストの最初の列でインデックスが作成された場合、2番目の列を引数リストに含めることはできません。  
  
 たとえば、sales order number 列と行番号列を SO_LINES テーブルの一意インデックスとして使用するには、ステートメントを使用します。  
  
```  
CREATE UNIQUE INDEX SO_LINES  
 ON SO_LINES (SONum, LineNum)  
```  
  
 Part number 列を SO_LINES テーブルの一意でないインデックスとして使用するには、ステートメントを使用します。  
  
```  
CREATE INDEX PartNum  
 ON SO_LINES (PartNum)  
```  
  
 2つの CREATE INDEX ステートメントを実行すると、最初のステートメントでは常にテーブルと同じ名前のプライマリインデックスが作成され、2番目のステートメントでは、列と同じ名前の一意でないインデックスが常に作成されることに注意してください。 CREATE INDEX ステートメントに異なる名前が入力されている場合や、2つ目の CREATE INDEX ステートメントで一意のラベルが付けられている場合でも、これらのインデックスはこのように名前が付けられます。  
  
> [!NOTE]  
>  Borland データベースエンジンを実装せずに Paradox ドライバーを使用する場合は、read ステートメントと append ステートメントのみが許可されます。
