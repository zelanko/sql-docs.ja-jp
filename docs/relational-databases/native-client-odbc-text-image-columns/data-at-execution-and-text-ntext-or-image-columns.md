---
title: 実行時のデータと Text、ntext、または Image 列 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
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
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: ae1060b6128a9adc67bfa79d127fd279c8f08905
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68128941"
---
# <a name="data-at-execution-and-text-ntext-or-image-columns"></a>実行時データと text 型、ntext 型、または image 型の列
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  ODBC 実行時データは、バインドされた列やパラメーターに対して、アプリケーションが大量のデータを操作できるようにする機能です。 非常に大きなを取得するときに**テキスト**、 **ntext**、または**イメージ**列アプリケーションできないことがありますを単純に巨大なバッファーを割り当てる、バッファーに列をバインドおよびフェッチ行。 非常に大きな更新するときに**テキスト**、 **ntext**、または**イメージ**列アプリケーションできない単純に巨大なバッファーを割り当てる、SQL ではパラメーター マーカーにバインドするにはステートメントでは、し、ステートメントを実行します。 このような場合は、アプリケーションを使用する必要があります[SQLGetData](../../relational-databases/native-client-odbc-api/sqlgetdata.md)または[SQLPutData](../../relational-databases/native-client-odbc-api/sqlputdata.md)その実行時データ オプションを使用します。  
  
## <a name="see-also"></a>関連項目  
 [text 列と image 列の管理](../../relational-databases/native-client-odbc-text-image-columns/managing-text-and-image-columns.md)  
  
  
