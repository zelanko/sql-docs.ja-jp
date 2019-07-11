---
title: インストール コンポーネント |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9d58b5791fc3cd6418f5594828aff6c8419cc7e1
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793415"
---
# <a name="installation-components"></a>インストール コンポーネント
> [!NOTE]  
>  ODBC は Windows XP および Windows Server 2003 以降、Windows オペレーティング システムに含まれます。 Windows の以前のバージョンで ODBC を明示的にのみインストールしてください。  
  
 ユーザーは、セットアップ プログラムを実行すると、インストール プロセスを開始します。 セットアップ プログラムの動作と組み合わせて、*インストーラー DLL*と*ドライバーのセットアップ DLL*ドライバーごとにします。 セットアップ プログラムと DLL のインストーラーの両方の引数を使用して、 **SQLInstallDriverEx**と**SQLInstallTranslatorEx**関数をコピーまたは削除の各コンポーネントのファイルを特定します。 次の図は、これらのインストール コンポーネント間の関係を示します。  
  
 ![インストール コンポーネント間の関係](../../../odbc/reference/install/media/pr29.gif "pr29")  
  
> [!IMPORTANT]
>  ODBC で使用されていた Odbc.inf ファイル*2.x*各 ODBC に必要なファイルを記述するコンポーネントで使用されていない ODBC *3.x*します。 付属の ODBC ドライバー *3.x*コンポーネントは Odbc.inf ファイルを作成する必要はありません。 削除**SQLInstallDriver**と**SQLInstallODBC**との非推奨**SQLInstallTranslator**が Odbc.inf の不要なレンダリングします。 ドライバー情報の Odbc.inf Driver キーワード節で説明するために使用するように提供されています、 *lpszDriver*引数**SQLInstallDriverEx**します。 Translator 情報 [ODBC トランスレーター] であるを使用して、Odbc.inf のトランスレーターの仕様のセクションに含まれるようになりました、 *lpszTranslator*の引数**SQLInstallTranslatorEx**します。 これらの変更は、プラットフォーム間で移植性を向上できる ODBC インストーラーを許可します。  
  
 これらのコンポーネントの詳細については、このセクションの最後に、次のトピックを参照してください。  
  
-   [セットアップ プログラム](../../../odbc/reference/install/setup-program.md)  
  
-   [インストーラー DLL](../../../odbc/reference/install/installer-dll.md)  
  
-   [ドライバーのセットアップ DLL](../../../odbc/reference/install/driver-setup-dll.md)
