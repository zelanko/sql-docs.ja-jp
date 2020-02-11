---
title: SQL Server Native Client 11.0 | での UTF-16 のサポートMicrosoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: f2520424-8ef4-409f-8147-d83da5076e96
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 415cb2fe8a3295770cfc8bd2d5c6e56750adb6d9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63205116"
---
# <a name="utf-16-support-in-sql-server-native-client-110"></a>SQL Server Native Client 11.0 での UTF-16 のサポート
  以降で[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]は、列の結果または出力パラメーターをバインドするときに固定長バッファーを指定し、 `wchar`終端文字の前にバッファーに書き込まれる文字がサロゲートペアの上位サロゲートコードポイントである場合、および`wchar`次の文字が下位サロゲートコードポイント[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]である場合、Native Client はバッファーに上位サロゲートコードポイントを追加しません。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client の機能](sql-server-native-client-features.md)  
  
  
