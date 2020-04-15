---
title: トランザクション | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- OLE DB, transactions
- transactions [OLE DB]
- SQL Server Native Client OLE DB provider, transactions
ms.assetid: 3b41e33a-c1ca-4b2a-9464-312b0ed3ca89
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 8779b68d6ab1070514f8ef6685ef378437d09539
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302536"
---
# <a name="transactions"></a>トランザクション
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアントの OLE DB プロバイダーは、ローカル トランザクションのサポートを実装します。 コンシューマーは、MS DTC (Microsoft 分散トランザクション コーディネーター) を使用して、分散トランザクションまたはコーディネートされたトランザクションを使用できます。 複数のセッションにまたがるトランザクション制御を必要とするコンシューマの場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント OLE DB プロバイダは、MS DTC によって開始および管理されるトランザクションに参加できます。  
  
 既定では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント OLE DB プロバイダは自動コミット トランザクション モードを使用[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]し、コンシューマ セッションの各個別アクションは のインスタンスに対する完全なトランザクションで構成されます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント OLE DB プロバイダーの自動コミット モードはローカルであり、自動コミット トランザクションは 1 セッション以上に及ぶことはありません。  
  
 ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント OLE DB プロバイダは**ITransactionLocal**インターフェイスを公開し、コンシューマがのインスタンスへの単一の接続で明示的および暗黙的にトランザクション[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を開始できるようにします。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ネイティブ クライアント OLE DB プロバイダーは、入れ子になったローカル トランザクションをサポートしていません。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [ローカル トランザクションのサポート](../../relational-databases/native-client-ole-db-transactions/supporting-local-transactions.md)  
  
-   [分散トランザクションのサポート](../../relational-databases/native-client-ole-db-transactions/supporting-distributed-transactions.md)  
  
-   [分離レベル &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-transactions/isolation-levels-ole-db.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client &#40;OLE DB&#41;](../../relational-databases/native-client/ole-db/sql-server-native-client-ole-db.md)  
  
  
