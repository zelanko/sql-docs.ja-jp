---
title: SQL Server テーブルの削除 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- tables [OLE DB]
- deleting tables
- SQL Server Native Client OLE DB provider, tables
- removing tables
- dropping tables
ms.assetid: b6d6c4de-43c6-473e-92aa-34ffddd58cbe
caps.latest.revision: 29
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c6bb2446d395b7c913653f7ac70805c5b0c5c050
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37408970"
---
# <a name="dropping-a-sql-server-table"></a>SQL Server テーブルの削除
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB プロバイダーが公開、 **itabledefinition::droptable**関数。 これにより、コンシューマーを削除する、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースからテーブル。  
  
 コンシューマーでは、テーブル名を指定の Unicode 文字の文字列として、 *pwszName*のメンバー、 *uName*共用体の*pTableID*パラメーター。 *EKind*のメンバー *pTableID* DBKIND_NAME にする必要があります。  
  
## <a name="see-also"></a>参照  
 [テーブルとインデックス](tables-and-indexes.md)  
  
  
