---
title: ストアド プロシージャ (OLE DB) を実行している |Microsoft ドキュメント
description: ストアド プロシージャの実行 (OLE DB)
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: ''
ms.component: ole-db
ms.reviewer: ''
ms.suite: sql
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- stored procedures [OLE DB], executing
- OLE DB, stored procedures
- OLE DB Driver for SQL Server, stored procedures
author: pmasl
ms.author: Pedro.Lopes
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e221429f88531e9cb4e47dd6adec346b786370b2
ms.sourcegitcommit: 9f4330a4b067deea396b8567747a6771f35e6eee
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/30/2018
---
# <a name="stored-procedures---running"></a>ストアド プロシージャの実行
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ステートメントを実行するときに、データ ソースではなく実行または直接クライアント アプリケーション内のステートメントを準備する) でストアド プロシージャの呼び出しを提供できます。  
  
-   パフォーマンスを向上します。  
  
-   ネットワーク オーバーヘッドの軽減します。  
  
-   一貫性の向上  
  
-   正確性の向上  
  
-   機能を追加します。  
  
 OLE DB Driver for SQL Server をサポートしている 3 つのメカニズムを[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データを返すストアド プロシージャを使用します。  
  
-   プロシージャ内のすべての SELECT ステートメントで結果セットを生成する。  
  
-   プロシージャが出力パラメーターによってデータを返すことができる。  
  
-   プロシージャに整数のリターン コードを含めることができる。  
  
 アプリケーションは、すべてのストアド プロシージャからこれらの出力を処理できる必要があります。  
  
 結果の処理中には、さまざまな OLE DB プロバイダーからさまざまなタイミングで出力パラメーターと戻り値が返されます。 OLE DB Driver for SQL Server が発生した場合、出力パラメーターとリターン コードはまで提供されません、コンシューマーが取得またはストアド プロシージャによって返される結果セットを取り消します。 これらのリターン コードと出力パラメーターは、サーバーからの最後の TDS パケットで返されます。  
  
 プロバイダーでは、DBPROP_OUTPUTPARAMETERAVAILABILITY プロパティを使用して、出力パラメーターと戻り値を返すタイミングを報告します。 このプロパティは、DBPROPSET_DATASOURCEINFO プロパティ セットに含まれています。  
  
 SQL Server の OLE DB Driver は、DBPROPVAL_OA_ATROWRELEASE を示すリターン コードと出力パラメーターは返されていないこと、結果セットが処理または解放されるまでに、DBPROP_OUTPUTPARAMETERAVAILABILITY プロパティを設定します。  
  
## <a name="see-also"></a>参照  
 [ストアド プロシージャ](../../oledb/ole-db/stored-procedures.md)  
  
  
