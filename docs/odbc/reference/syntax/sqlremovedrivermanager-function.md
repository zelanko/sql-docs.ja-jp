---
title: 関数を削除する |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLRemoveDriverManager
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLRemoveDriverManager
helpviewer_keywords:
- SQLRemoveDriverManager function function [ODBC]
ms.assetid: 3a41511f-6603-4b81-a815-7883874023c4
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 27b32c1c4e0f3f4d5359af287ba07d40b033af00
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301813"
---
# <a name="sqlremovedrivermanager-function"></a>SQLRemoveDriverManager 関数
**適合 性**  
 バージョンの導入: ODBC 3.0: Windows XP サービス パック 2、Windows Server 2003 サービス パック 1、および以降のオペレーティング システムで非推奨。  
  
 **まとめ**  
 システム情報**の**Odbcinst.ini エントリから ODBC コア コンポーネントに関する情報を変更または削除します。  
  
## <a name="syntax"></a>構文  
  
```cpp  
  
BOOL SQLRemoveDriverManager(  
     LPDWORD     pdwUsageCount);  
```  
  
## <a name="arguments"></a>引数  
 *を使用します。*  
 [出力]この関数が呼び出された後のドライバー マネージャーの使用カウント。  
  
## <a name="returns"></a>戻り値  
 関数は成功した場合は TRUE を返し、失敗した場合は FALSE を返します。 この関数が呼び出されたときにシステム情報にエントリが存在しない場合、この関数は FALSE を返します。  
  
## <a name="diagnostics"></a>診断  
 **SQL を****呼び出**すことによって、関連付けられている*\*pfErrorCode*値を取得できます。 次の表は **、SQLInstallerError***\** によって返される可能性のある pfErrorCode 値の一覧であり、この関数のコンテキストでそれぞれについて説明します。  
  
|*\*エラーコード*|エラー|説明|  
|---------------------|-----------|-----------------|  
|ODBC_ERROR_GENERAL_ERR|インストーラの一般的なエラー|特定のインストーラ エラーが発生しなかったエラーが発生しました。|  
|ODBC_ERROR_COMPONENT_NOT_FOUND|レジストリにコンポーネントが見つかりません|レジストリに存在しないか、またはレジストリに見つからなかったため、インストーラーはドライバ マネージャ情報を削除できませんでした。|  
|ODBC_ERROR_USAGE_UPDATE_FAILED|コンポーネントの使用カウントをインクリメントまたはデクリメントできませんでした|インストーラーは、ドライバー マネージャーの使用カウントを減らすに失敗しました。|  
|ODBC_ERROR_OUT_OF_MEM|メモリ不足|メモリ不足のため、インストーラは機能を実行できませんでした。|  
  
## <a name="comments"></a>説明  
 **関数****を補完**し、システム情報のコンポーネントの使用カウントを更新します。 この関数は、セットアップ アプリケーションからのみ呼び出す必要があります。  
  
 **コア**コンポーネントの使用率カウントを 1 減らす。 コンポーネントの使用率カウントが 0 になると、入力システム情報は削除されます。 コア コンポーネントエントリは、システム情報の次の場所にある"ODBC Core"というタイトルの下にあります。  
  
 `HKEY_LOCAL_MACHINE`  
  
 `SOFTWARE`  
  
 `ODBC`  
  
 `Odbcinst.ini`  
  
> [!CAUTION]  
>  コンポーネントの使用数とファイルの使用数がゼロに達すると、アプリケーションは、ドライバー マネージャーのファイルを物理的に削除しないでください。  
  
 **実際**にはファイルは削除されません。 呼び出し側プログラムは、ファイルの削除とファイル使用量カウントの維持を担当します。 ただし、コンポーネントの使用カウントとファイル使用量カウントの両方がゼロに達した場合、Driver Manager ファイルは削除しないでください。  
  
 **アンインストール**プロセスの一部として呼び出されます。 ODBC コア コンポーネント (ドライバー マネージャー、カーソル ライブラリ、インストーラー、言語ライブラリ、管理者、サンクファイルなど) は、全体としてアンインストールされます。 アンインストール プロセスの一部として**呼**び出された場合、次のファイルは削除されません。  
  
|||  
|-|-|  
|ODBC32DLL|ODBCCP32.Dll|  
|ODBCCR32.Dll|ODBC16GT。Dll|  
|ODBCCU32.Dll|ODBC32GT。Dll|  
|ODBCINT.Dll|DS16GT.Dll|  
|ODBCTRAC。Dll|DS32GT。Dll|  
|MSVCRT40.Dll|ODBCAD32.Exe|  
|ODBCCP32.Cpl||  
  
 **アップグレード**プロセスの一部として呼び出されます。 アプリケーションがアップグレードを実行する必要があることを検出し、以前にドライバをインストールした場合は、ドライバを削除してから再インストールする必要があります。  
  
 最初**に呼**び出して、コンポーネントの使用カウントを減らす必要があります。 次に、コンポーネント**の**使用カウントをインクリメントするために呼び出す必要があります。 アプリケーションセットアッププログラムは、古いコアコンポーネントファイルを新しいファイルで置き換える必要があります。 ファイル使用量カウントは同じままで、古いバージョンのコア コンポーネント ファイルを使用する他のアプリケーションは新しいバージョンのファイルを使用します。  
  
## <a name="related-functions"></a>関連する関数  
  
|対象|参照先|  
|---------------------------|---------|  
|ドライバ マネージャのインストール|[ドライバー マネージャー](../../../odbc/reference/syntax/sqlinstalldrivermanager-function.md)|
