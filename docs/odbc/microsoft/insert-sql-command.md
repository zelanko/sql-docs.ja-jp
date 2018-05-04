---
title: SQL コマンドを挿入 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- INSERT [ODBC]
ms.assetid: 9b648198-349f-46f6-b869-13d129945971
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 881ee4d74eab6b1e26b1f3ec243a39c08125ea00
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="insert---sql-command"></a>SQL コマンドを挿入します。
指定したフィールドの値を含むテーブルの最後にレコードを追加します。  
  
 Visual FoxPro ODBC ドライバーでは、このコマンドのネイティブの Visual FoxPro 言語の構文をサポートしています。 ドライバー固有の情報は、「解説」を参照してください。  
  
## <a name="syntax"></a>構文  
  
```  
  
INSERT INTO dbf_name [(fname1 [, fname2, ...])]  
   VALUES (eExpression1 [, eExpression2, ...])  
```  
  
## <a name="arguments"></a>引数  
 INSERT INTO *dbf_name*  
 新しいレコードを追加するテーブルの名前を指定します。 *dbf_name*パスを含めることができ、名前の式を指定できます。  
  
 指定したテーブルが開いていない場合、新しい作業領域に排他的に開かれていると、テーブルに新しいレコードが追加されます。 新しい作業領域が選択されていません。現在の作業領域では、選択されたままです。  
  
 指定したテーブルが開いている場合は、INSERT は、テーブルに新しいレコードを追加します。 現在の作業領域以外のテーブルが作業領域で開いている場合は、選択されていない後、レコードが追加されます。現在の作業領域では、選択されたままです。  
  
 [( *fname1*[、 *fname2*[,...])]  
 新しいレコードのフィールドの名前を指定に値が挿入されます。  
  
 値 ( *eExpression1*[、 *eExpression2*[,...])  
 新しいレコードに挿入されたフィールドの値を指定します。 フィールド名を省略した場合は、テーブルの構造によって定義された順序でフィールド値を指定する必要があります。  
  
## <a name="remarks"></a>解説  
 新しいレコードには、VALUES 句のリストにあるデータが含まれています。  
  
## <a name="driver-remarks"></a>ドライバーの解説  
 アプリケーションは、データ ソースに挿入の ODBC SQL ステートメントを送信するとき、Visual FoxPro ODBC ドライバーを翻訳しないで Visual FoxProINSERT コマンドにコマンドに変換します。  
  
## <a name="see-also"></a>参照  
 [テーブルの SQL コマンドを作成します。](../../odbc/microsoft/create-table-sql-command.md)   
 [SELECT - SQL コマンド](../../odbc/microsoft/select-sql-command.md)
