---
title: インストールコンポーネント |Microsoft Docs
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
ms.openlocfilehash: 34d1b6d143f6f40d73e2feeb0b718f3c3b3248fe
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68094129"
---
# <a name="installation-components"></a>インストール コンポーネント
> [!NOTE]  
>  Windows XP および windows Server 2003 以降では、ODBC は Windows オペレーティングシステムに含まれています。 ODBC は、以前のバージョンの Windows にのみ明示的にインストールする必要があります。  
  
 ユーザーがセットアッププログラムを実行すると、インストールプロセスが開始されます。 セットアッププログラムは、各ドライバーの*インストーラー dll*および*ドライバーセットアップ dll*と連携して動作します。 セットアッププログラムとインストーラー DLL の両方で、 **Sqlinstalldriverex**関数と**SQLInstallTranslatorEx**関数の引数を使用して、各コンポーネントでコピーまたは削除するファイルを決定します。 次の図は、これらのインストールコンポーネント間の関係を示しています。  
  
 ![インストール コンポーネント間の関係](../../../odbc/reference/install/media/pr29.gif "pr29")  
  
> [!IMPORTANT]
>  Odbc 2.x では、各 ODBC コンポーネントに必要なファイルを*記述するために odbc .inf*ファイルが使用されていますが、odbc *3. x*では使用されません。 ODBC 3.x コンポーネントを出荷するドライバーでは *、odbc .inf*ファイルを作成する必要はありません。 **Sqlinstalldriver**と**SQLInstallODBC**の削除、および**sqlinstalldriver**が廃止されたため、Odbc が不要になりました。 Odbc の Driver キーワードセクションに含まれていたドライバー情報が、 **Sqlinstalldriverex**の*lpszdriver*引数に指定されるようになりました。 Odbc の [ODBC Translator] セクションおよび Translator Specification セクションに含まれていた変換情報が、 **SQLInstallTranslatorEx**の*lpsztranslator*引数に指定されるようになりました。 これらの変更により、プラットフォーム間での ODBC インストーラーの移植性が向上します。  
  
 これらのコンポーネントの詳細については、このセクションの最後にある次のトピックを参照してください。  
  
-   [セットアップ プログラム](../../../odbc/reference/install/setup-program.md)  
  
-   [インストーラー DLL](../../../odbc/reference/install/installer-dll.md)  
  
-   [ドライバーのセットアップ DLL](../../../odbc/reference/install/driver-setup-dll.md)
