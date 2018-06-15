---
title: 並列データ ウェアハウスのエラー メッセージ |Microsoft ドキュメント
description: 並列データ ウェアハウス (PDW) エラー メッセージがエラーを報告および問題 PDW コンポーネントで発生した PDW を通じて表示される SQL Server のエラーを含めることもできます。 これらのエラー メッセージは、情報を表すための一貫性のある構文を使用します。 この構文を理解することを特定し、問題を解決できるようにします。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 33bdf11388ae52959d264e2df091e9c9669b159b
ms.sourcegitcommit: 056ce753c2d6b85cd78be4fc6a29c2b4daaaf26c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/19/2018
ms.locfileid: "31539072"
---
# <a name="error-messages-in-parallel-data-warehouse"></a>Parallel Data Warehouse でのエラー メッセージ

並列データ ウェアハウス (PDW) エラー メッセージがエラーを報告および問題 PDW コンポーネントで発生した PDW を通じて表示される SQL Server のエラーを含めることもできます。 これらのエラー メッセージは、情報を表すための一貫性のある構文を使用します。 この構文を理解することを特定し、SQL Server PDW 上の問題を解決できるようにします。  
  
## <a name="Basics"></a>エラー メッセージの基本事項  
返されるエラー メッセージでは、同じ構文に従います。  
  
`Error_Indicator [SQL_State_Code] [Driver_Details] [QueryID] Message_String`  
  
これらは、各フィールドの潜在的な値です。  
  
|フィールド|Description|例|  
|---------|---------------|-----------|  
|*Error_Indicator*|"ERROR"という単語またはその他のテキストを問題をユーザーに警告します。|ERROR|  
|*SQL_State_Code*|SQL 状態コード、ODBC 仕様に従ったです。 ドライバーは、いつでもアプリケーションにメッセージを返します、適切な SQL 状態コードを生成します。 テキスト"Microsoft"では、エラーの原因を示します。|42000|  
|*Driver_Details*|ドライバーに依存するなどの詳細を使用するドライバーの種類。|ODBC SQL Server 2008 R2 並列データ ウェアハウス ドライバー|  
|*QueryID*|クエリの一意の識別子。 クエリの処理に関連するその他の情報を検索するのにには、この値を使用します。 たとえば、クエリ実行の詳細は含まれて、管理コンソール クエリ ID を使用します。 詳細については、次を参照してください。[アプライアンスを管理コンソールを使用して監視](monitor-the-appliance-by-using-the-admin-console.md)です。<br /><br />QueryID が適用されない場合は、「内部」のテキストがユーザーに返されます。|QID2377|  
|*Message_String*|エラーまたは問題の人間が判読できる説明。 SQL Server のエラーを返すときに、SQL Server のメッセージ テキストになります。|等号代入のみが、UPDATE ステートメントの set リストに表示できます。|  
  
これらの値の例は、次のように、ユーザーに提示は。  
  
`ERROR [42000] [Microsoft][ODBC SQL Server 2008 R2 Parallel Data Warehouse driver][QID2380]Only equal assignment can appear in the set list of an UPDATE statement.`  
  
## <a name="see-also"></a>参照  
<!-- MISSING LINKS 
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
[管理コンソールのアラートをについてください。](understanding-admin-console-alerts.md)  
  
