---
title: FILESTREAM データの部分的な更新 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-blob
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- FILESTREAM [SQL Server], FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT
- FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT
ms.assetid: d6f7661e-6c14-4d31-9541-4520ca0f82b2
caps.latest.revision: 15
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c59d3e7823efe62ecb7227eab605af23a6ea3112
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36070961"
---
# <a name="make-partial-updates-to-filestream-data"></a>FILESTREAM データの部分的な更新
  アプリケーションでは、FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT を使用して FILESTREAM BLOB データを部分的に更新します。 [DeviceIoControl](http://go.microsoft.com/fwlink/?LinkId=105527) 関数は、この値と、 [OpenSqlFilestream](access-filestream-data-with-opensqlfilestream.md) から FILESTREAM ドライバーに返されるハンドルを渡します。 このドライバーによって、サーバー側の現在の FILESTREAM データが、ハンドルが参照するファイルにコピーされます。 ハンドルへの書き込みが行われた後にアプリケーションが FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT 値を発行すると、最後の書き込み操作は維持され、それより前のハンドルへの書き込み操作は失われます。  
  
> [!NOTE]  
>  FILESTREAM のリモート アクセスは、 [SMB プロトコル](http://go.microsoft.com/fwlink/?LinkId=112454) に依存しています。  
  
## <a name="example"></a>例  
 次の例では、 `FSCTL_SQL_FILESTREAM_FETCH_OLD_CONTENT` 値を使用して、挿入された FILESTREAM BLOB を部分的に更新する方法を示します。  
  
> [!NOTE]  
>  この例では、「 [FILESTREAM が有効なデータベースを作成する方法](create-a-filestream-enabled-database.md) 」および「 [FILESTREAM データを格納するテーブルを作成する方法](create-a-table-for-storing-filestream-data.md)」で作成した、FILESTREAM が有効なデータベースとテーブルが必要です。  
  
 [!code-cpp[FILESTREAM#FS_CPP_FSCTL](../../snippets/tsql/SQL15/tsql/filestream/cpp/filestream.cpp#fs_cpp_fsctl)]  
  
## <a name="see-also"></a>参照  
 [OpenSqlFilestream による FILESTREAM データへのアクセス](access-filestream-data-with-opensqlfilestream.md)   
 [FILESTREAM データ用のクライアント アプリケーションの作成](create-client-applications-for-filestream-data.md)  
  
  