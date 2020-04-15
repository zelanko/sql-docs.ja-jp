---
title: ICommand::Execute を使用した行セットの作成 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], creating
- SQL Server Native Client OLE DB provider, rowsets
- OLE DB rowsets, creating
- Execute method
ms.assetid: 9b530b7d-8165-49d4-a978-5ced17c6705e
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 0658928bcf1e4ee5fd67e3c934cd589cc13a28b3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286812"
---
# <a name="creating-rowsets-with-icommandexecute"></a>ICommand::Execute を使用した行セットの作成
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  **ICommand::Execute** メソッドを使用して作成された行セットの場合、結果の行セットに設定するプロパティで、コマンドのテキストを制約できます。 これは、動的コマンド テキストをサポートするコンシューマーにとって特に重要です。  
  
 ネイティブ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]クライアント OLE DB[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]プロバイダは、カーソルを使用して、多くのコマンドによって生成される複数行セットの結果をサポートすることはできません。 コンシューマーが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] カーソル サポートを必要とする行セットを要求した場合に、コマンド テキストが結果として複数行を生成すると、エラーが発生します。 詳細については、「[複数行セットの結果を生成するコマンド](../../relational-databases/native-client-ole-db-commands/commands-generating-multiple-rowset-results.md)」を参照してください。  
  
 スクロール可能[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]なネイティブ クライアント OLE DB プロバイダー[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]行セットは、カーソルでサポートされています。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、他のデータベース ユーザーの変更によって影響を受けるカーソルに制限が設けらます。 たとえば、一部のカーソル内の行は順序付けできません。この場合に、SQL ORDER BY 句を含むコマンドを使用して行セットを作成しようとすると、エラーが発生します。 詳細については、「[行セットと SQL Server カーソル](../../relational-databases/native-client-ole-db-rowsets/rowsets-and-sql-server-cursors.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [行セット](../../relational-databases/native-client-ole-db-rowsets/rowsets.md)  
  
  
