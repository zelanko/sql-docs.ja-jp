---
title: ストアド プロシージャ (OLE DB) の実行 |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: native-client-ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- stored procedures [OLE DB], executing
- OLE DB, stored procedures
- SQL Server Native Client OLE DB provider, stored procedures
ms.assetid: c77d9be9-2176-4438-8c7a-04b63ebece08
caps.latest.revision: 30
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: ed9df8c1c51143442b622e9aa14831ede809a1b6
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37415401"
---
# <a name="stored-procedures---running"></a>ストアド プロシージャ - 実行
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  ステートメントを実行するときに (実行または直接クライアント アプリケーションでステートメントの準備) せずに、データ ソースのストアド プロシージャの呼び出しを指定できます。  
  
-   高いパフォーマンス。  
  
-   ネットワーク オーバーヘッドの軽減します。  
  
-   一貫性の向上  
  
-   正確性の向上  
  
-   機能を追加します。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは 3 つのメカニズムをサポートしているを[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データを返すストアド プロシージャを使用します。  
  
-   プロシージャ内のすべての SELECT ステートメントで結果セットを生成する。  
  
-   プロシージャが出力パラメーターによってデータを返すことができる。  
  
-   プロシージャに整数のリターン コードを含めることができる。  
  
 アプリケーションは、すべてのストアド プロシージャからこれらの出力を処理できる必要があります。  
  
 結果の処理中には、さまざまな OLE DB プロバイダーからさまざまなタイミングで出力パラメーターと戻り値が返されます。 場合、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーでは、出力パラメーターおよびリターン コードが指定されていないまで、コンシューマーが取得またはストアド プロシージャによって返される結果セットが取り消されました。 これらのリターン コードと出力パラメーターは、サーバーからの最後の TDS パケットで返されます。  
  
 プロバイダーでは、DBPROP_OUTPUTPARAMETERAVAILABILITY プロパティを使用して、出力パラメーターと戻り値を返すタイミングを報告します。 このプロパティは、DBPROPSET_DATASOURCEINFO プロパティ セットに含まれています。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーは、DBPROP_OUTPUTPARAMETERAVAILABILITY プロパティを DBPROPVAL_OA_ATROWRELEASE を示すリターン コードと出力パラメーターは返されないこと、結果セットが処理または解放されるまでに設定します。  
  
## <a name="see-also"></a>参照  
 [ストアド プロシージャ](../../../relational-databases/native-client/ole-db/stored-procedures.md)  
  
  
