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
ms.openlocfilehash: af8581071400db888fb508b88f8e8ae93bc71f70
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85039001"
---
# <a name="utf-16-support-in-sql-server-native-client-110"></a>SQL Server Native Client 11.0 での UTF-16 のサポート
  以降では [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 、列の結果または出力パラメーターをバインドするときに固定長バッファーを指定し、 `wchar` 終端文字の前にバッファーに書き込まれる文字がサロゲートペアの上位サロゲートコードポイントである場合、および次の文字が下位サロゲートコードポイントである場合、 `wchar` [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client はバッファーに上位サロゲートコードポイントを追加しません。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client の機能](sql-server-native-client-features.md)  
  
  
