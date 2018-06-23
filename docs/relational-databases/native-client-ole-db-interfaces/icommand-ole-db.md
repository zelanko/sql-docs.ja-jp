---
title: ICommand (OLE DB) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ICommand [SQL Server Native Client]
ms.assetid: 5e24b3a0-0658-44fc-b653-f4c52f9eb328
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 9805a573b71996aa4628a5ad2f2f648c0c5bb710
ms.sourcegitcommit: a78fa85609a82e905de9db8b75d2e83257831ad9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2018
ms.locfileid: "35700843"
---
# <a name="icommand-ole-db"></a>ICommand (OLE DB)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  このトピックでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client に固有の OLE DB の動作について説明します。  
  
## <a name="icommandexecute"></a>ICommand::Execute  
 列のサイズより大きなデータを挿入すると、通常はエラーが発生します。 ただし、S_OK が返される状況がありますが、 *dwStatus* DBSTATUS_S_TRUNCATED に設定されます。 これは、一般的に発生するパラメーターを使用してデータを挿入するときに列がないデータを保持するのに十分な大きさであると**icommandwithparameters::setparameterinfo**が呼び出されていません。  
  
## <a name="see-also"></a>参照  
 [インターフェイス&#40;OLE DB&#41;](http://msdn.microsoft.com/library/34c33364-8538-45db-ae41-5654481cda93)  
  
  
