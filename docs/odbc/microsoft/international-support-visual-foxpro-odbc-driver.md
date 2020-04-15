---
title: インターナショナル サポート (ビジュアル フォックスプロ ODBC ドライバー) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- double-byte character sets [ODBC]
- FoxPro ODBC driver [ODBC], international support
- DBCS [ODBC]
- international support [ODBC]
- sort order [ODBC]
- collating sequences [ODBC]
- Visual FoxPro ODBC driver [ODBC], international support
ms.assetid: cd3fab32-13f1-4a86-abc4-5e18667669fc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b4b0c758bb478ea6a468e6756c3d6f0f52c766f5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299972"
---
# <a name="international-support-visual-foxpro-odbc-driver"></a>国際化サポート (Visual FoxPro ODBC ドライバー)
マイクロソフト ビジュアル フォックスプロ ODBC ドライバーは、次をサポートしています。  
  
-   2 バイト文字セット (DBCS)  
  
-   複数の照合順序  
  
 照合順序は、Visual FoxPro テーブルまたはデータベースに格納されているデータの*並べ替え順序*を定義します。 既定では、ドライバーは、オペレーティング システムの言語バージョンをサポートする照合シーケンスを使用するように構成されています。  
  
 サポートされる照合シーケンスのリストについては[、SET COLLATE](../../odbc/microsoft/set-collate-command.md)を参照してください。  
  
## <a name="locale"></a>locale  
 指定された言語と国/地域に対応する情報のセット。 ロケールは、小数点区切り記号、日付と時刻の形式、文字の並べ替え順序などの特定の設定を示します。  
  
## <a name="sort-order"></a>並べ替え順 (sort order)  
 並べ替え順には、異なる*ロケール*の並べ替え規則が組み込まれており、それらの言語のデータを正しく並べ替えることができます。 Visual FoxPro では、現在の並べ替え順序によって、文字式の比較の結果と、インデックス付きまたは並べ替えられたテーブルでのレコードの表示順序が決まります。
