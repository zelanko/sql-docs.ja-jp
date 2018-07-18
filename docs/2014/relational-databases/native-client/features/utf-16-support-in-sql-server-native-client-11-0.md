---
title: SQL Server Native Client 11.0 での utf-16 のサポート |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: native-client  - "database-engine" - "docset-sql-devref"
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: f2520424-8ef4-409f-8147-d83da5076e96
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 59079427bc0a8e1c62bf9b3590073e35ac2ed6b1
ms.sourcegitcommit: f8ce92a2f935616339965d140e00298b1f8355d7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/03/2018
ms.locfileid: "37423521"
---
# <a name="utf-16-support-in-sql-server-native-client-110"></a>SQL Server Native Client 11.0 での UTF-16 のサポート
  以降で[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]場合、および列の結果または出力パラメーターをバインドするときに、固定長バッファーを指定した場合、`wchar`終端文字がサロゲート ペアの上位サロゲート コード ポイントの前に、バッファーに書き込まれた文字次`wchar`文字が下位サロゲート コード ポイントでは、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client はバッファーに上位サロゲート コード ポイントを追加できません。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client の機能](sql-server-native-client-features.md)  
  
  
