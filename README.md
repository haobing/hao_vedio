# hao_vedio
HTTP Live Streaming直播关键技术步骤：

采集视频源和音频源的数据
对原始数据进行H264（视频）编码和AAC（音频）编码
视频和音频数据封装为MPEG-TS包
HLS分段生成策略及m3u8索引文件
HTTP传输协议

*一个网络中可以有多个TS流(用PAT中的ts_id区分)
 *  一个TS流中可以有多个频道(用PAT中的pnumber、pmt_pid区分)
 *  一个频道中可以有多个PES流(用PMT中的mpt_stream区分)
 TS文件判断的方法一般为前5个包都是188字节(0x47开头，2..5*188都是0x47)，则认为是包大小为188字节
 
 
 解析TS流数据的流程：查找PID为0x0的包，解析PAT，PAT包中的program_map_PID表示PMT的PID；
 查找PMT，PMT包中的elementary_PID表示音视频包的PID，PMT包中的PCR_PID表示PCR的PID，
 有的时候PCR的PID跟音频或者视频的PID相同，说明PCR会融进音视频的包，注意解析，有的时候PCR是自己单独的包；CAT、NIT、SDT、EIT的PID分别为: 0x01、0x10、0x11、0x12。

 
