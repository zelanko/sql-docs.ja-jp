---
title: インストール コンポーネント |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- installing ODBC components [ODBC], setup program
- ODBC [ODBC], component installation
ms.assetid: 9de15ca0-fe6a-4634-8709-a928d3c9cc73
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1c5fe2538d1567630121f05a4798583099de7200
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32917207"
---
# <a name="installation-components"></a>インストール コンポーネント
> [!NOTE]  
>  Windows XP および Windows Server 2003 以降、Windows オペレーティング システムに ODBC が含まれます。 以前のバージョンの Windows で ODBC を明示的にのみインストールしてください。  
  
 ユーザーは、セットアップ プログラムを実行すると、インストール プロセスを開始します。 セットアップ プログラムの動作と組み合わせて、*インストーラー DLL*と*ドライバーのセットアップ DLL*ドライバーごとにします。 セットアップ プログラムと DLL のインストーラーの両方の引数を使用して、 **SQLInstallDriverEx**と**SQLInstallTranslatorEx**をコピーまたは削除の各コンポーネントのファイルを特定する関数。 次の図は、これらのインストール コンポーネント間の関係を示します。  
  
 ![インストール コンポーネント間の関係](../../../odbc/reference/install/media/pr29.gif "pr29")  
  
> [!IMPORTANT]  
>  ODBC 2 で使用されていた Odbc.inf ファイルです。*x*を必要とされる各 ODBC でファイルを記述するコンポーネントで使用されていない ODBC 3 *.x*です。 ODBC 3 を添付されているドライバー *.x*コンポーネントは、Odbc.inf ファイルを作成する必要はありません。 削除**SQLInstallDriver**と**SQLInstallODBC**との非推奨**SQLInstallTranslator**が Odbc.inf の不要な表示します。 ドライバー情報の Odbc.inf Driver キーワード セクションに存在するために使用するように提供されています、 *lpszDriver*引数**SQLInstallDriverEx**です。 [ODBC 変換者] 内にある変換プログラム情報を使用して、Odbc.inf の変換プログラムの仕様のセクションで提供されるよう、 *lpszTranslator*の引数**SQLInstallTranslatorEx**です。 これらの変更は、プラットフォーム間で移植性を向上できる ODBC インストーラーを許可します。  
  
 これらのコンポーネントに関する詳細については、このセクションの最後に、次のトピックを参照してください。  
  
-   [セットアップ プログラム](../../../odbc/reference/install/setup-program.md)  
  
-   [インストーラー DLL](../../../odbc/reference/install/installer-dll.md)  
  
-   [ドライバーのセットアップ DLL](../../../odbc/reference/install/driver-setup-dll.md)
