---
title: 実行時データと Text、ntext、または Image 型の列 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- text columns [ODBC]
- SQL Server Native Client ODBC driver, image columns
- SQL Server Native Client ODBC driver, text columns
- data types [ODBC], image
- data types [ODBC], text
- columns [ODBC]
- ODBC data types, image columns
- ODBC data types, text columns
- data-at-execution
- ODBC data-at-execution
- image columns [ODBC]
ms.assetid: 67ffb1a6-f38d-4712-ba64-96bdd41ec2b2
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7e7c57cf6444e5833b6deee0dcae36d71b7a6430
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "63195129"
---
# <a name="data-at-execution-and-text-ntext-or-image-columns"></a>実行時データと text 型、ntext 型、または image 型の列
  ODBC 実行時データは、バインドされた列やパラメーターに対して、アプリケーションが大量のデータを操作できるようにする機能です。 非常に大きな**text**型、 **ntext**型、または**image**型の列を取得する場合、アプリケーションは単純に大きなバッファーを割り当てて、その列をバッファーにバインドし、行をフェッチすることができない可能性があります。 非常に大きな**text**型、 **ntext**型、または**image**型の列を更新する場合、アプリケーションは単純に大きなバッファーを割り当てて、それを SQL ステートメントのパラメーターマーカーにバインドした後、ステートメントを実行できない可能性があります。 このような場合、アプリケーションでは、実行時データオプションを使用して[SQLGetData](../native-client-odbc-api/sqlgetdata.md)または[sqlputdata](../native-client-odbc-api/sqlputdata.md)を使用する必要があります。  
  
## <a name="see-also"></a>参照  
 [text 列と image 列の管理](managing-text-and-image-columns.md)  
  
  
