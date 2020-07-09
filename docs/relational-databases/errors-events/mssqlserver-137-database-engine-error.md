---
title: MSSQLSERVER_137 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 137 (Database Engine error)
ms.assetid: 47fb4212-2165-4fec-bc41-6d548465d7be
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 834f3e28b8e368b29c2465f44f6a23528ad32626
ms.sourcegitcommit: da88320c474c1c9124574f90d549c50ee3387b4c
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/01/2020
ms.locfileid: "85781081"
---
# <a name="mssqlserver_137"></a>MSSQLSERVER_137
 [!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]
  
## <a name="details"></a>詳細  
  
| 属性 | 値 |  
| :-------- | :---- |  
|製品名|SQL Server|  
|イベント ID|137|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|P_SCALAR_VAR_NOTFOUND|  
|メッセージ テキスト|スカラー変数 "% * ls" を宣言してください。|  
  
## <a name="explanation"></a>説明  
このエラーは、SQL スクリプトで、変数を宣言する前にその変数を使用しようとした場合に発生します。 次の例では、SET ステートメントおよび SELECT ステートメントの両方でエラー 137 が発生します。これは **\@mycol** が宣言されていないためです。  
  
SET @mycol = 'ContactName';  
  
SELECT @mycol;  
  
このエラーのより複雑な原因の 1 つは、EXECUTE ステートメントの外部で宣言された変数を使用することです。 たとえば、SELECT ステートメントで指定した変数 **\@mycol** は、SELECT ステートメントのローカル変数であり、EXECUTE ステートメントにとっては外部の変数です。  
  
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
[EXECUTE &#40;Transact-SQL&#41;](~/t-sql/language-elements/execute-transact-sql.md)  
[SET ステートメント &#40;Transact-SQL&#41;](~/t-sql/statements/set-statements-transact-sql.md)  
[DECLARE @local_variable &#40;Transact-SQL&#41;](~/t-sql/language-elements/declare-local-variable-transact-sql.md)  
  
