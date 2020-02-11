---
title: バインドされたテキストと画像の列 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
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
- image columns [ODBC]
ms.assetid: ffd3442e-d880-46e9-b848-2365a09a2406
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1bf8ac0cf868394d9aa8063220939feee69ac2f6
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62626585"
---
# <a name="bound-vs-unbound-text-and-image-columns"></a>バインドされた text、image 型の列とバインドされない text、image 型の列
  サーバーカーソルを使用する場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 、NATIVE Client ODBC ドライバーは、 **sqlfetch**の実行時に、バインドされていない**text**、 **ntext**、または**image**型の列のデータを転送しないように最適化されています。 **Text**型、 **ntext**型、または**image**型のデータは、アプリケーションが列に対して[SQLGetData](../native-client-odbc-api/sqlgetdata.md)を発行するまで、実際にはサーバーから取得されません。  
  
 ユーザーがカーソル内を上下にスクロールしている間に、 **text**、 **ntext**、または**image**データが表示されないように、多くのアプリケーションを記述できます。 ユーザーが行を選択して詳細を取得すると、アプリケーションは**SQLGetData**を呼び出して、 **text**、 **ntext**、または**image**データを取得できます。 これにより、ユーザーが選択していない行の**text**型、 **ntext**型、または**image**型のデータが転送されるのを防ぐことができるため、非常に大量のデータの転送を防ぐことができます。  
  
## <a name="see-also"></a>参照  
 [Text 列と Image 列の管理](managing-text-and-image-columns.md)   
 [カーソル動作](../native-client-odbc-cursors/cursor-behaviors.md)  
  
  
