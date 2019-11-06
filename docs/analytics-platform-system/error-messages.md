---
title: Parallel Data Warehouse のエラー メッセージ |Microsoft Docs
description: 並列データ ウェアハウス (PDW) エラー メッセージがエラーを報告し、問題の PDW コンポーネントで発生したし、PDW を通じて表示される SQL Server のエラーを含めることもできます。 これらのエラー メッセージでは、一貫性のある構文を使用して情報を表すため。 この構文を理解することができますを特定し、問題を修正します。
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 78c5cd8dab37ac9cb32de794861c68e6c8085747
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67960969"
---
# <a name="error-messages-in-parallel-data-warehouse"></a>Parallel Data Warehouse でのエラー メッセージ

並列データ ウェアハウス (PDW) エラー メッセージがエラーを報告し、問題の PDW コンポーネントで発生したし、PDW を通じて表示される SQL Server のエラーを含めることもできます。 これらのエラー メッセージでは、一貫性のある構文を使用して情報を表すため。 この構文を理解することができますを特定し、SQL Server PDW の問題を修正します。  
  
## <a name="Basics"></a>エラー メッセージの基本  
返されるエラー メッセージでは、同じ構文に従います。  
  
`Error_Indicator [SQL_State_Code] [Driver_Details] [QueryID] Message_String`  
  
これらは、各フィールドの潜在的な値です。  
  
|フィールド|説明|例|  
|---------|---------------|-----------|  
|*Error_Indicator*|"ERROR"という単語、またはその他のテキストが、問題をユーザーに警告します。|ERROR|  
|*SQL_State_Code*|SQL 状態コード、ODBC 仕様です。 ドライバーは、いつでもアプリケーションにメッセージを返します、適切な SQL 状態コードを生成します。 テキスト"Microsoft"では、エラーの原因を示します。|42000|  
|*Driver_Details*|ドライバーに依存するなどの詳細を使用するドライバーの種類。|ODBC SQL Server 2008 R2 Parallel Data Warehouse のドライバー|  
|*QueryID*|クエリの一意の識別子。 クエリの処理に関連するのに追加の情報を見つけるには、この値を使用します。 たとえば、クエリ実行の詳細があります管理コンソールでクエリの id。 詳細については、次を参照してください。[アプライアンスの監視、管理コンソールを使用して](monitor-the-appliance-by-using-the-admin-console.md)します。<br /><br />QueryID が適用されない場合は、ユーザーに「内部」のテキストが返されます。|QID2377|  
|*Message_String*|エラーまたは問題の人間が判読できる説明。 SQL Server のエラーを返すときに SQL Server のメッセージ テキストになります。|UPDATE ステートメントの set リストには等号代入のみが表示されます。|  
  
これらの例の値は、このようなユーザーに表示する場合します。  
  
`ERROR [42000] [Microsoft][ODBC SQL Server 2008 R2 Parallel Data Warehouse driver][QID2380]Only equal assignment can appear in the set list of an UPDATE statement.`  
  
## <a name="see-also"></a>参照  
<!-- MISSING LINKS 
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
[管理コンソールのアラートをについてください。](understanding-admin-console-alerts.md)  
  
