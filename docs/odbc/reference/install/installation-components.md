---
title: インストール コンポーネント |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- installing ODBC components [ODBC], setup program
- ODBC [ODBC], component installation
ms.assetid: 9de15ca0-fe6a-4634-8709-a928d3c9cc73
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0a196e9b935229fa03c6dd0eda92b8e99e69f0ca
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285252"
---
# <a name="installation-components"></a>インストール コンポーネント
> [!NOTE]  
>  WINDOWS XP および Windows Server 2003 以降では、ODBC が Windows のオペレーション システムに含まれています。 ODBC は、以前のバージョンの Windows にのみ明示的にインストールしてください。  
  
 ユーザーがセットアップ プログラムを実行すると、インストール プロセスが開始されます。 セットアップ プログラムは *、インストーラー DLL*と各*ドライバーのドライバーセットアップ DLL*と連携して動作します。 セットアップ プログラムとインストーラー DLL の両方で **、SQLInstallDriverEx**関数と**SQLInstallTranslatorEx**関数の引数を使用して、各コンポーネントのコピーまたは削除するファイルを決定します。 次の図は、これらのインストール コンポーネント間の関係を示しています。  
  
 ![インストール コンポーネント間の関係](../../../odbc/reference/install/media/pr29.gif "pr29")  
  
> [!IMPORTANT]
>  ODBC *2.x*で各 ODBC コンポーネントで必要なファイルを記述するために使用された ODBC.inf ファイルは、ODBC *3.x*では使用されません。 ODBC *3.x*コンポーネントを出荷するドライバーは、Odbc.inf ファイルを作成する必要はありません。 **SQL インストールドライバー**と SQL**インストールODBC**の削除と SQL**インストールトランスレータ**の廃止により、Odbc.inf は不要になりました。 Odbc.inf のドライバー キーワードセクションに含まれているドライバー情報は **、SQLInstallDriverEx**の*引数 lpszDriver*に指定されました。 Odbc.inf の [ODBC 変換プログラム] セクションと変換プログラム仕様のセクションに含まれている変換プログラム情報が、 **SQLInstallTranslatorEx**の*lpszTranslator*引数に指定されました。 これらの変更により、ODBC インストーラはプラットフォーム間で移植性を高めます。  
  
 これらのコンポーネントの詳細については、このセクションの最後にある次のトピックを参照してください。  
  
-   [セットアップ プログラム](../../../odbc/reference/install/setup-program.md)  
  
-   [インストーラー DLL](../../../odbc/reference/install/installer-dll.md)  
  
-   [ドライバーのセットアップ DLL](../../../odbc/reference/install/driver-setup-dll.md)
