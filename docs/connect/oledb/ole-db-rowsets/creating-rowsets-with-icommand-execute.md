---
title: Icommand::execute で行セットの作成 |Microsoft Docs
description: ICommand::Execute を使用した行セットの作成
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- rowsets [OLE DB], creating
- OLE DB Driver for SQL Server, rowsets
- OLE DB rowsets, creating
- Execute method
author: pmasl
ms.author: pelopes
manager: craigg
ms.openlocfilehash: 86de5c5e985d038ec4e2640fcd9d4d87b56546d5
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47773826"
---
# <a name="creating-rowsets-with-icommandexecute"></a>ICommand::Execute を使用した行セットの作成
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  **ICommand::Execute** メソッドを使用して作成された行セットの場合、結果の行セットに設定するプロパティで、コマンドのテキストを制約できます。 これは、動的コマンド テキストをサポートするコンシューマーにとって特に重要です。  
  
 OLE DB Driver for SQL Server は、多数のコマンドで生成される複数の行セット結果をサポートする場合に、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] カーソルを使用できません。 コンシューマーが [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] カーソル サポートを必要とする行セットを要求した場合に、コマンド テキストが結果として複数行を生成すると、エラーが発生します。 詳細については、次を参照してください。[コマンドを生成する複数の行セット結果](../../oledb/ole-db-commands/commands-generating-multiple-rowset-results.md)します。  
  
 サポートされているスクロール可能な OLE DB Driver for SQL Server の行セット[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]カーソル。 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] では、他のデータベース ユーザーの変更によって影響を受けるカーソルに制限が設けらます。 たとえば、一部のカーソル内の行は順序付けできません。この場合に、SQL ORDER BY 句を含むコマンドを使用して行セットを作成しようとすると、エラーが発生します。 詳細については、「[行セットと SQL Server カーソル](../../oledb/ole-db-rowsets/rowsets-and-sql-server-cursors.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [行セット](../../oledb/ole-db-rowsets/rowsets.md)  
  
  
