---
title: SQL Server ネイティブ クライアント 11.0 での UTF-16 のサポート |マイクロソフトドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: f2520424-8ef4-409f-8147-d83da5076e96
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 56a368c8b01e1afec2fab5de5eb3c575c6ebdf14
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303166"
---
# <a name="utf-16-support-in-sql-server-native-client-110"></a>SQL Server Native Client 11.0 での UTF-16 のサポート
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]以降、列の結果または出力パラメーターをバインドするときに固定長バッファーを指定した場合、ターミネータ文字の前にバッファーに書き込まれる **wchar** 文字がサロゲート ペアの上位サロゲート コード ポイントである場合、および次の **wchar** 文字が下位サロゲート コード ポイントである場合は、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client はバッファーに上位サロゲート コード ポイントを追加しません。  
  
## <a name="see-also"></a>参照  
 [SQL Server Native Client の機能](../../../relational-databases/native-client/features/sql-server-native-client-features.md)  
  
  
