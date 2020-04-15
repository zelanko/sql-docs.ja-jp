---
title: 挿入 - SQL コマンド |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- INSERT [ODBC]
ms.assetid: 9b648198-349f-46f6-b869-13d129945971
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ce00005fb1aa0ca9732fc5e9cfeacd6faf6ef9e1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300009"
---
# <a name="insert---sql-command"></a>INSERT - SQL コマンド
指定したフィールド値を含むテーブルの末尾にレコードを追加します。  
  
 ビジュアル フォックスプロ ODBC ドライバーは、このコマンドのネイティブの Visual FoxPro 言語構文をサポートしています。 ドライバ固有の情報については、「解説」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```  
  
INSERT INTO dbf_name [(fname1 [, fname2, ...])]  
   VALUES (eExpression1 [, eExpression2, ...])  
```  
  
## <a name="arguments"></a>引数  
 *dbf_name*に挿入  
 新しいレコードが追加されるテーブルの名前を指定します。 *dbf_name*パスを含めることができ、名前式を指定できます。  
  
 指定したテーブルが開いていない場合は、新しい作業領域で排他的に開かれ、新しいレコードがテーブルに追加されます。 新しい作業領域が選択されていません。現在の作業領域は選択されたままです。  
  
 指定したテーブルが開いている場合、INSERT は新しいレコードをテーブルに追加します。 テーブルが現在の作業領域以外の作業領域で開かれている場合、レコードが追加された後は選択されません。現在の作業領域は選択されたままです。  
  
 [(fname1[、fname2[.]] *fname1* *fname2*  
 新しいレコードで、値が挿入されるフィールドの名前を指定します。  
  
 値 ( *e 式1*[, *eExpression2*,.])  
 新しいレコードに挿入されるフィールド値を指定します。 フィールド名を省略する場合は、テーブル構造で定義された順序でフィールド値を指定する必要があります。  
  
## <a name="remarks"></a>解説  
 新しいレコードには、VALUES 句にリストされているデータが含まれます。  
  
## <a name="driver-remarks"></a>ドライバの解説  
 アプリケーションが ODBC SQL ステートメント INSERT をデータ ソースに送信すると、変換なしでコマンドが Visual FoxProINSERT コマンドに変換されます。  
  
## <a name="see-also"></a>参照  
 [テーブルの作成 - SQL コマンド](../../odbc/microsoft/create-table-sql-command.md)   
 [SELECT - SQL コマンド](../../odbc/microsoft/select-sql-command.md)
