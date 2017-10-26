---
title: "互換性対応表 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- driver compatibility issues [ODBC]
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], application and driver compatibility
- compatibility [ODBC], application and driver compatibility
- application compatibility issues [ODBC]
- application upgrades [ODBC], compatibility matrix
- upgrading applications [ODBC], compatibility matrix
ms.assetid: 0690b463-15a1-48fa-9d0b-9cc9e5bf7fc6
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 8c980058ea2cacba7b9160571b1b42884ea02e41
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="compatibility-matrix"></a>互換性マトリックス
次の表では、アプリケーションやドライバーのこのセクションで以前定義の型の互換性について説明します。  
  
|アプリケーションの種類<br /><br /> バージョン|32 ビット ODBC<br /><br /> 2.*x*ドライバー|ODBC 3 です。*x*<br /><br /> ドライバー●どらいば○|ODBC 3.8 ドライバー|ISO 準拠しているオープン グループ – ドライバー|  
|--------------------------------------|-----------------------------------|---------------------------|---------------------|-----------------------------------------|  
|16 ビット アプリケーションで、任意のバージョン|互換性のあります。|互換性のあります。|互換性のあります。|互換性のあります。|  
|純粋な 2 になります。*x*アプリケーション|互換性のあります。|互換性のあります。|互換性のあります。|いない互換性のある [3]|  
|純粋な 2 になります。*x*アプリケーションを再コンパイル|互換性のあります。|互換性のある [1]|互換性のある [1]|いない互換性のある [3]|  
|純粋な 2 になります。*x* Unicode アプリケーション|互換性のあります。|互換性のある [1]|互換性のある [1]|いない互換性のある [3]|  
|純粋なグループと ISO に準拠したアプリケーション|互換性がありません。|互換性のある [2]|互換性のある [2]|互換性のある [2]|  
|純粋な 3.0 アプリケーション|互換性がありません。|互換性のあります。|互換性のあります。|いない互換性のある [4]|  
|純粋な 3.5 アプリケーション|互換性がありません。|互換性のあります。|互換性のあります。|いない互換性のある [4]|  
|純粋な 3.8 (またはそれ以降) のアプリケーション|いない互換性のある [5]|いない互換性のある [5]|互換性のあります。|いない互換性のある [4]|  
|置き換えられるアプリケーション|互換性のあります。|互換性のあります。|互換性のあります。|いない互換性のある [3]|  
  
 [1] で、アプリケーションを (Unicode アプリケーションの場合) は、UNICODE オプションを使用して ODBC 3.5 (またはそれ以降) のヘッダーを使用して再コンパイルする必要があります 0x0250 に ODBCVER を設定する必要があります。  
  
 [2] で、アプリケーションは、ODBC 3.5 (またはそれ以降) のヘッダーを使用してコンパイルする必要があり、ODBC ドライバー マネージャーとをリンクします。 ヘッダー フラグ ODBC_STD 設定することもあります。  
  
 [3] この構成可能性のある ODBC 2 で機能があるために、機能があります。*x*ブックマークなど、標準に含まれていません。  
  
 [ODBC 3 の機能があるために、機能を 4] この構成が失敗する可能性のある*.x*ブックマークなど、標準に含まれていません。  
  
 [ODBC 3.8 ODBC 2.x または 3.x ドライバー、ドライバー固有の仕様などに含まれていない機能があるためにが、5] この構成に失敗する可能性があることができます[ODBC における C データ型](../../../odbc/reference/develop-app/c-data-types-in-odbc.md)です。  
  
## <a name="driver-manager-compatibility"></a>ドライバー マネージャーの互換性  
 すべてのドライバー マネージャーのバージョンで動作する必要がある ODBC 3.0 アプリケーションの起動時に次の操作をする必要があります。  
  
-   環境ハンドルを割り当てます。  
  
-   また環境属性を SQL_OV_ODBC3_80 に設定します。 ドライバー マネージャーでは、SQL_ERROR が返された場合、ドライバー マネージャーは 3.8 より古いです。 ドライバー マネージャーに対応する、必要に応じてを SQL_OV_ODBC3 または SQL_OV_ODBC2、またをリセットします。  
  
-   接続ハンドルを割り当てます。  
  
-   接続を作成します。  
  
-   ドライバーのバージョンを特定 SQL_DRIVER_ODBC_VER の SQLGetInfo を呼び出します。 ODBC 3.8 ドライバーをドライバーには、ドライバー固有の C 型を使用することができます。 それ以外の場合、ドライバー固有の C データ型を使わないでください。  
  
 ただし、再コンパイルされた ODBC 3.x アプリケーションはまたの SQL_OV_ODBC3_80 を指定せず、このドライバー固有の C 型以外の ODBC 3.8 機能を使用できます。 これは、ODBC 3.x 機能を使用して、再コンパイルされた ODBC 2.x アプリケーションに似ています。  
  
## <a name="using-sqlcancelhandle-in-an-application-compatible-with-all-driver-managers"></a>アプリケーションと互換性のあるすべてのドライバー マネージャーの SQLCancelHandle の使用  
 [SQLCancelHandle 関数](../../../odbc/reference/syntax/sqlcancelhandle-function.md)はサポートされていない Windows 7 以前にリリースされたドライバー マネージャー、アプリケーションでは読み込めません古いバージョンの Windows が呼び出す場合**SQLCancelHandle**直接です。 ドライバー マネージャーのすべてのバージョンを使用して、 **SQLCancelHandle**新しいバージョンの Windows では、アプリケーションを呼び出す必要があります**SQLCancelHandle**を使用して直接**LoadLibrary**と**GetProcAddress です。**  
  
## <a name="see-also"></a>参照  
 [ODBC 3.8 の新機能](../../../odbc/reference/what-s-new-in-odbc-3-8.md)

