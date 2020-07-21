---
title: MSSQLSERVER_137 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 137 (Database Engine error)
ms.assetid: 47fb4212-2165-4fec-bc41-6d548465d7be
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 72e0b54f26c323c16efa8c67aea1c325e8ddf72d
ms.sourcegitcommit: b57d98e9b2444348f95c83a24b8eea0e6c9da58d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/21/2020
ms.locfileid: "86552289"
---
# <a name="mssqlserver_137"></a>MSSQLSERVER_137
    
## <a name="details"></a>詳細  
  
|属性|値|  
|-|-|  
|製品名|SQL Server|  
|イベント ID|137|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|P_SCALAR_VAR_NOTFOUND|  
|メッセージ テキスト|スカラー変数 "% * ls" を宣言してください。|  
  
## <a name="explanation"></a>説明  
 このエラーは、SQL スクリプトで、変数を宣言する前にその変数を使用しようとした場合に発生します。 次の例で **@mycol** は、が宣言されていないため、SET ステートメントと SELECT ステートメントの両方に対してエラー137が返されます。  
  
 SET @mycol = 'ContactName';  
  
 SELECT @mycol;  
  
 このエラーのより複雑な原因の 1 つは、EXECUTE ステートメントの外部で宣言された変数を使用することです。 たとえば、 **@mycol** select ステートメントで指定された変数は、select ステートメントに対してローカルであるため、EXECUTE ステートメントの外部にあります。  
  
 USE AdventureWorks2012;  
  
 GO  
  
 DECLARE @mycol nvarchar(20);  
  
 SET @mycol = 'Name';  
  
 EXECUTE ('SELECT @mycol FROM Production.Product;');  
  
## <a name="user-action"></a>ユーザーの操作  
 SQL スクリプトで使用する変数がスクリプト内の別の場所で事前に宣言されていることを確認します。  
  
 外部で宣言された EXECUTE ステートメント内の変数を参照しないようにスクリプトを修正します。 次に例を示します。  
  
 USE AdventureWorks2012;  
  
 GO  
  
 DECLARE @mycol nvarchar(20) ;  
  
 SET @mycol = 'Name';  
  
 EXECUTE ('SELECT ' + @mycol + ' FROM Production.Product';) ;  
  
## <a name="see-also"></a>参照  
 [EXECUTE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/execute-transact-sql)   
 [SET ステートメント &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-statements-transact-sql)   
 [DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql)  
  
  
