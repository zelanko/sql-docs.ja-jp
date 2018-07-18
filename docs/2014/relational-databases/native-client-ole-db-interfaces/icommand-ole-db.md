---
title: ICommand (OLE DB) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- ICommand [SQL Server Native Client]
ms.assetid: 5e24b3a0-0658-44fc-b653-f4c52f9eb328
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d4af8804173ac33cacba69d633d16fb48912edc7
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37415661"
---
# <a name="icommand-ole-db"></a>ICommand (OLE DB)
  このトピックでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client に固有の OLE DB の動作について説明します。  
  
## <a name="icommandexecute"></a>ICommand::Execute  
 列のサイズより大きなデータを挿入すると、通常はエラーが発生します。 ただし、S_OK が返される場合がありますが、 *dwStatus* DBSTATUS_S_TRUNCATED に設定されます。 これは通常、データに対して列のサイズが不十分であり、`ICommandWithParameters::SetParameterInfo` が呼び出されていない場合に、データをパラメーターで挿入すると発生します。  
  
## <a name="see-also"></a>参照  
 [インターフェイス&#40;OLE DB&#41;](../../database-engine/dev-guide/interfaces-ole-db.md)  
  
  
