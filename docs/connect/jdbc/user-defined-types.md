---
title: ユーザー定義型 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 19a71b27-b788-43a3-a76d-fe3001a6f016
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 72dca79e295f54d4c01421ef79408008bd559210
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="user-defined-types"></a>ユーザー定義型
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  ユーザー定義型 (Udt) で導入された[!INCLUDE[ssVersion2005](../../includes/ssversion2005_md.md)]で共通言語ランタイム (CLR) オブジェクトを格納することにより、サーバーのスカラー型システムを拡張する開発者を許可する、[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]データベース。 Udt は複数の要素を含めることができ、でき、1 つで構成される従来の別名データ型とは異なり、動作[!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]システム データ型。 従来、UDT のサイズは最大 8 KB に制限されていました。 [!INCLUDE[ssKatmai](../../includes/sskatmai_md.md)]、64 キロバイトを超える Udt のサポートが追加されました。 バージョン 3.0 以降の JDBC Driver も、UserDefined 形式を指定する場合に、64 KB を超える UDT をサポートするようになりました。  
  
 8,000 バイト以下の UDT の動作は従来と変わりませんが、8,000 バイトを超える UDT もサポートされるようになり、そのサイズは "無制限" として報告されます。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーのデータ型について](../../connect/jdbc/understanding-the-jdbc-driver-data-types.md)  
  
  
