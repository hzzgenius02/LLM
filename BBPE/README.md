| BBPE 特性        | 代码位置                                                                                                 |
|----------------|------------------------------------------------------------------------------------------------------|
| 操作字节级别而非字符     | bytes_to_unicode 中构建字节到 Unicode 的映射，token.encode('utf-8') 对字符编码为字节流。                                 |
| 能处理任意符号（非标准字符） | bytes_to_unicode 映射 0-255 字节到独特 Unicode 字符，支持 Emoji、特殊符号等。                                           |
| 通过字节对合并构建分词单元  | bpe 方法通过 get_pairs 找到字节对，按 self.bpe_ranks 优先级合并，逐步构建分词。                                              |
| 适配性和可逆性        | 编码：''.join(self.byte_encoder[b] for b in token.encode('utf-8'))；解码：bytearray([...]).decode('utf-8')。 |
