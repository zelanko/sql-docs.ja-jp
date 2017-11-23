---
title: "エラー メッセージ (SQL Server PDW)"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.prod: sql-non-specified
ms.prod_service: mpp-data-warehouse
ms.service: 
ms.component: analytics-platform-system
ms.technology: mpp-data-warehouse
ms.custom: 
ms.date: 01/13/2017
ms.reviewer: na
ms.suite: sql
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e6223cba-2dec-4b8a-bc10-e2ef6a821fe0
caps.latest.revision: "9"
ms.openlocfilehash: 7c7d453bc2ac68db724734d7db7cf58e35611ba8
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="error-messages"></a>エラー メッセージ
SQL Server PDW エラー メッセージがエラーを報告し、問題が、SQL Server PDW コンポーネントによって発生し、SQL Server PDW を通じて表示される SQL Server のエラーを含めることもできます。 これらのエラー メッセージは、情報を表すための一貫性のある構文を使用します。 この構文を理解することを特定し、SQL Server PDW 上の問題を解決できるようにします。  
  
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
  
