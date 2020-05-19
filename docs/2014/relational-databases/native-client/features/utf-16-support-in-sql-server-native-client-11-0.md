---
title: SQL Server Native Client 11.0 | での UTF-16 のサポートMicrosoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: f2520424-8ef4-409f-8147-d83da5076e96
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: b28d869a6e33969550751158e321ec24062bf6ac
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/01/2020
ms.locfileid: "82707157"
---
# <a name="utf-16-support-in-sql-server-native-client-110"></a>SQL Server Native Client 11.0 での UTF-16 のサポート
  以降では [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 、列の結果または出力パラメーターをバインドするときに固定長バッファーを指定し、 `wchar` 終端文字の前にバッファーに書き込まれる文字がサロゲートペアの上位サロゲートコードポイントである場合、および次の文字が下位サロゲートコードポイントである場合、 `wchar` [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client はバッファーに上位サロゲートコードポイントを追加しません。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client の機能](sql-server-native-client-features.md)  
  
  
