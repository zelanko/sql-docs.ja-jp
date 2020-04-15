---
title: 互換性マトリックス |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver compatibility issues [ODBC]
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], application and driver compatibility
- compatibility [ODBC], application and driver compatibility
- application compatibility issues [ODBC]
- application upgrades [ODBC], compatibility matrix
- upgrading applications [ODBC], compatibility matrix
ms.assetid: 0690b463-15a1-48fa-9d0b-9cc9e5bf7fc6
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0406599e1657a900d1669861572ff13834cec670
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307455"
---
# <a name="compatibility-matrix"></a>互換性マトリックス
次の表では、このセクションで前に定義したアプリケーションとドライバーの種類の互換性について説明します。  
  
|アプリケーションの種類<br /><br /> とバージョン|32 ビット ODBC<br /><br /> *2.x*ドライバ|ODBC *3.x*<br /><br /> ドライバー●どらいば○|ODBC 3.8 ドライバ|ISOとオープングループ準拠のドライバ|  
|--------------------------------------|-----------------------------------|---------------------------|---------------------|-----------------------------------------|  
|16 ビット アプリケーション、任意のバージョン|互換性あり|互換性あり|互換性あり|互換性あり|  
|純粋な*2.x*アプリケーション|互換性あり|互換性あり|互換性あり|互換性がありません[3]|  
|純粋な*2.x*再コンパイルされたアプリケーション|互換性あり|互換性[1]|互換性[1]|互換性がありません[3]|  
|純粋な*2.x*ユニコード アプリケーション|互換性あり|互換性[1]|互換性[1]|互換性がありません[3]|  
|純粋なオープングループとISO準拠のアプリケーション|互換性なし|互換性[2]|互換性[2]|互換性[2]|  
|ピュア 3.0 アプリケーション|互換性なし|互換性あり|互換性あり|互換性がない[4]|  
|ピュア 3.5 アプリケーション|互換性なし|互換性あり|互換性あり|互換性がない[4]|  
|純粋な 3.8 (またはそれ以上) アプリケーション|互換性がありません [5]|互換性がありません [5]|互換性あり|互換性がありません [4]|  
|置き換えられたアプリケーション|互換性あり|互換性あり|互換性あり|互換性がありません[3]|  
  
 [1] アプリケーションは、UNICODE オプション (Unicode アプリケーションの場合) を使用して ODBC 3.5 (またはそれ以降) のヘッダーを使用して再コンパイルする必要があり、ODBCVER を 0x0250 に設定する必要があります。  
  
 [2] アプリケーションは、ODBC 3.5 (またはそれ以降) のヘッダーを使用してコンパイルし、ODBC ドライバー マネージャーとリンクする必要があります。 また、ヘッダフラグODBC_STDを設定する必要があります。  
  
 [3] この設定は、ODBC *2.x*に、標準にはない機能 (ブックマークなど) が存在するため、動作しない可能性があります。  
  
 [4] この設定は、ODBC *3.x*に、標準にはない機能 (ブックマークなど) が存在するため、動作しない可能性があります。  
  
 ODBC 3.8 には ODBC 2.x または 3.x ドライバにはない機能 (ODBC のドライバ固有[の C データ型](../../../odbc/reference/develop-app/c-data-types-in-odbc.md)など) が存在するため、この設定が失敗する可能性があります。  
  
## <a name="driver-manager-compatibility"></a>ドライバー マネージャーの互換性  
 すべてのドライバー マネージャーのバージョンで動作する必要がある ODBC 3.0 アプリケーションは、起動時に次の操作を行う必要があります。  
  
-   環境ハンドルを割り当てます。  
  
-   SQL_ATTR_ODBC_VERSION環境属性をSQL_OV_ODBC3_80に設定します。 ドライバー マネージャーがSQL_ERRORを返す場合、ドライバー マネージャーは 3.8 より古いです。 SQL_ATTR_ODBC_VERSIONをSQL_OV_ODBC3またはSQL_OV_ODBC2にリセットし、必要に応じてドライバ マネージャに対応します。  
  
-   接続ハンドルを割り当てます。  
  
-   接続を確立します。  
  
-   ドライバーのバージョンを確認するには、SQL_DRIVER_ODBC_VERの SQLGetInfo を呼び出します。 ドライバーが ODBC 3.8 ドライバーの場合は、ドライバー固有の C 型を使用できます。 それ以外の場合は、ドライバー固有の C データ型を使用しないでください。  
  
 再コンパイルされた ODBC 3.x アプリケーションでは、SQL_ATTR_ODBC_VERSIONに対してSQL_OV_ODBC3_80を指定しなくても、ドライバー固有の C 型以外の ODBC 3.8 機能を使用できます。 これは、ODBC 3.x 機能を使用して再コンパイルされた ODBC 2.x アプリケーションに似ています。  
  
## <a name="using-sqlcancelhandle-in-an-application-compatible-with-all-driver-managers"></a>すべてのドライバー マネージャーと互換性のあるアプリケーションで SQLCancelHandle を使用する  
 [SQLCancelHandle 関数](../../../odbc/reference/syntax/sqlcancelhandle-function.md)は、Windows 7 より前にリリースされたドライバー マネージャーではサポートされていないため、**アプリケーションは、アプリケーションは、直接 SQLCancelHandle**を呼び出す場合は、Windows の古いバージョンで読み込むことはできません。 ドライバー マネージャーのすべてのバージョンを使用して、新しいバージョンの Windows で**SQLCancelHandle**を使用するには、アプリケーションは **、読み込みライブラリ**と**GetProcAddress**を使用して間接的に**SQLCancelHandle**を呼び出す必要があります。  
  
## <a name="see-also"></a>参照  
 [ODBC 3.8 の新機能](../../../odbc/reference/what-s-new-in-odbc-3-8.md)
