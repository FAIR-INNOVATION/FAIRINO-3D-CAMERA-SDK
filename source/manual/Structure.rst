数据结构
=========

.. toctree:: 
    :maxdepth: 5

相机设备信息
------------------
.. c:type:: tSdkCameraDevInfo

   相机设备信息结构体。
   
   .. list-table:: 结构体成员说明
      :widths: 25 25 50
      :header-rows: 1
      
      * - 成员名称
        - 数据类型
        - 描述
      * - ``cameraSn``
        - ``char[32]``
        - 相机序列号
      * - ``cameraIP``
        - ``char[128]``
        - 相机IP地址
      * - ``cameraType``
        - ``char[32]``
        - 相机型号
      * - ``cameraFWVersion``
        - ``char[32]``
        - 相机固件版本
      * - ``irCameraResWidth``
        - ``int``
        - 红外图像宽度（像素）
      * - ``irCameraResHeight``
        - ``int``
        - 红外图像高度（像素）
      * - ``rgbCameraResWidth``
        - ``int``
        - 彩色图像宽度（像素）
      * - ``rgbCameraResHeight``
        - ``int``
        - 彩色图像高度（像素）
      * - ``projectorBatch``
        - ``char[32]``
        - 投影模块批次
      * - ``projectorFWVersion``
        - ``char[32]``
        - 投影机固件版本
      * - ``projectorFlashState``
        - ``int``
        - 投影机闪存状态
图像帧头信息
------------------
.. c:type:: tSdkFrameHead

   帧头信息结构体，包含图像数据的元数据信息。
   
   .. list-table:: 结构体成员说明
      :widths: 25 20 55
      :header-rows: 1
      
      * - 成员名称
        - 数据类型
        - 描述
      * - ``iStx``
        - ``uint16_t``
        - 起始标识符
      * - ``iType``
        - ``uint16_t``
        - 大类型（2D图、3D图）
      * - ``iPointCloudDataType``
        - ``uint32_t``
        - 点云数据类型（X、Y、Z）
      * - ``iTimeStamp``
        - ``uint64_t``
        - 该帧的采集时间
      * - ``iDataSize``
        - ``uint32_t``
        - 数据总大小（字节）
      * - ``iPointDataSize``
        - ``uint32_t``
        - 点云数据大小（字节）
      * - ``iIRWidth``
        - ``uint32_t``
        - IR图像的宽度（像素）
      * - ``iIRHeight``
        - ``uint32_t``
        - IR图像的高度（像素）
      * - ``iIRDataSize``
        - ``uint32_t``
        - IR图像数据大小（字节）
      * - ``iRGBWidth``
        - ``uint32_t``
        - RGB图像的宽度（像素）
      * - ``iRGBHeight``
        - ``uint32_t``
        - RGB图像的高度（像素）
      * - ``iRGBDataSize``
        - ``uint32_t``
        - RGB图像数据大小（字节）
      * - ``fCameraTemperature``
        - ``float``
        - 相机温度（摄氏度）
数据获取设置参数
------------------
.. c:type:: tSdkSendPCDParam

   点云数据发送参数配置结构体。
   
   .. list-table:: 结构体成员说明
      :widths: 25 20 30 25
      :header-rows: 1
      
      * - 成员名称
        - 数据类型
        - 描述
        - 默认值/范围
      * - ``iTriggerMode``
        - ``uint16_t``
        - 触发模式
        - 0：单次触发、1：连续触发
      * - ``iProjectorMode``
        - ``uint16_t``
        - 投影模式
        - 0：快速、1：正常、2：高精度
      * - ``iSerialNumber``
        - ``uint8_t``
        - 串口号
        - 0
      * - ``iIRResolutionMode``
        - ``uint8_t``
        - 双目相机分辨率模式
        - 0：默认分辨率、1：Binning
      * - ``iRGBResolutionMode``
        - ``uint8_t``
        - 彩色分辨率模式
        - 0：不输出RGB、1：默认、2：Binning
      * - ``iIRExposureCount``
        - ``uint8_t``
        - 双目相机曝光次数
        - 1~3
      * - ``iIRExposureTimes1``
        - ``uint32_t``
        - 双目相机曝光时间1
        - 10000μs
      * - ``iIRExposureTimes2``
        - ``uint32_t``
        - 双目相机曝光时间2
        - 10000μs
      * - ``iIRExposureTimes3``
        - ``uint32_t``
        - 双目相机曝光时间3
        - 10000μs
      * - ``fIRGain``
        - ``float``
        - 双目相机增益
        - 2.5x
      * - ``iRGBExposureTimes``
        - ``uint32_t``
        - 彩色相机曝光时间
        - 10000μs
      * - ``fRGBGain``
        - ``float``
        - 彩色相机增益
        - 2.5x
      * - ``iIRWhiteExpo``
        - ``uint32_t``
        - 双目相机灰图曝光
        - 2500μs
      * - ``fIRWhiteGain``
        - ``float``
        - 双目相机灰图增益
        - 2.5x
结构光模式数据处理参数
--------------------
.. c:type:: tSdkCameraComputeParameterInfo

   相机计算参数信息结构体，用于配置点云计算的各项参数。
   
   .. list-table:: 结构体成员说明
      :widths: 25 20 25 30
      :header-rows: 1
      
      * - 成员名称
        - 数据类型
        - 默认值
        - 描述
      * - ``iThr_num``
        - ``uint32_t``
        - 180
        - 杂点过滤阈值，数值越小过滤杂点越少（最小为0）
      * - ``fMaxDiff``
        - ``float``
        - 0.5
        - 最大差异阈值，数值越大过滤杂点越少（最小为0）
      * - ``fPhase_LR``
        - ``float``
        - 0.5
        - 相位匹配参数，数值越大有效值越多（最小为0）
      * - ``fModulation``
        - ``float``
        - 0
        - 调制参数，数值越小有效值越多（最小为0）
      * - ``iDepthMin``
        - ``uint32_t``
        - 300
        - 最小测量距离（单位：毫米）
      * - ``iDepthMax``
        - ``uint32_t``
        - 1300
        - 最大测量距离（单位：毫米）
线扫模式数据处理参数
--------------------
.. c:type:: tSdkCameraLineComputeParameterInfo

   相机线计算参数信息结构体，用于配置线激光计算的各项参数。
   
   .. list-table:: 结构体成员说明
      :widths: 28 18 18 36
      :header-rows: 1
      
      * - 成员名称
        - 数据类型
        - 默认值
        - 描述
      * - ``Thr_num_line``
        - ``uint32_t``
        - 200
        - 杂点过滤阈值（count），默认100
      * - ``maxDiff_line``
        - ``float``
        - 0.25
        - 杂点过滤阈值，默认0.5
      * - ``threshold``
        - ``float``
        - 1
        - 视察图过滤阈值，默认1
      * - ``img_thrd``
        - ``float``
        - 20
        - 中心线提取阈值（0~255），数值越大中心线越小，计算速度越快
      * - ``default_prj_light``
        - ``uint32_t``
        - -
        - 判断是否属于亮度增强版本（仅针对130J版本）
      * - ``default_gain_set``
        - ``uint32_t``
        - -
        - 判断相机增益配置是否产生变化（版本≥2.2.07表明增益有变化，仅针对130J版本）
      * - ``kernel_Gauss_mode``
        - ``int``
        - -
        - 平滑系数（可选0、1、2）
      * - ``filter_num``
        - ``int``
        - 3
        - 假数据过滤参数，范围[0, 10]
双目标定内外参
--------------------
无RGB模式内参
--------------------
.. c:type:: tSdkCameraCalibration_IR_IR

   双目红外相机标定参数结构体，包含左右相机的内参、外参和畸变参数。
   
   .. list-table:: 标定参数结构体
      :widths: 25 20 55
      :header-rows: 1
      
      * - 成员名称
        - 数据类型
        - 描述
      * - **左相机参数**
        - 
        - 
      * - ``fc_left``
        - ``double[2]``
        - 左相机焦距 (fx, fy)
      * - ``cc_left``
        - ``double[2]``
        - 左相机主点坐标 (cx, cy)
      * - ``kc_left``
        - ``double[5]``
        - 左相机畸变系数 [k1, k2, p1, p2, k3]
      * - ``R_left``
        - ``double[9]``
        - 左相机旋转矩阵 (3×3)
      * - ``alpha_c_left``
        - ``double``
        - 左相机倾斜系数
      * - **右相机参数**
        - 
        - 
      * - ``fc_right``
        - ``double[2]``
        - 右相机焦距 (fx, fy)
      * - ``cc_right``
        - ``double[2]``
        - 右相机主点坐标 (cx, cy)
      * - ``kc_right``
        - ``double[5]``
        - 右相机畸变系数 [k1, k2, p1, p2, k3]
      * - ``R_right``
        - ``double[9]``
        - 右相机旋转矩阵 (3×3)
      * - ``alpha_c_right``
        - ``double``
        - 右相机倾斜系数
      * - **新标定参数**
        - 
        - 
      * - ``fc_left_new``
        - ``double[2]``
        - 左相机新焦距 (fx, fy)
      * - ``cc_left_new``
        - ``double[2]``
        - 左相机新主点坐标 (cx, cy)
      * - ``fc_right_new``
        - ``double[2]``
        - 右相机新焦距 (fx, fy)
      * - ``cc_right_new``
        - ``double[2]``
        - 右相机新主点坐标 (cx, cy)
      * - ``kc_new``
        - ``double[2]``
        - 新畸变系数 [k1, k2]
      * - ``R_new``
        - ``double[9]``
        - 新旋转矩阵 (3×3)
      * - ``T_new``
        - ``double[3]``
        - 新平移向量 (tx, ty, tz)
RGB相机内参
--------------------
.. c:type:: tSdkCameraCalibration_IR_RGB

   红外与彩色相机联合标定参数结构体，包含IR和RGB相机的内外参数。
   
   .. list-table:: IR-RGB相机标定参数
      :widths: 25 20 20 35
      :header-rows: 1
      
      * - 成员名称
        - 数据类型
        - 数组大小
        - 描述
      * - **IR相机参数**
        - 
        - 
        - 
      * - ``fc_left``
        - ``double``
        - 2
        - IR相机焦距 (fx, fy)
      * - ``cc_left``
        - ``double``
        - 2
        - IR相机主点坐标 (cx, cy)
      * - ``kc_left``
        - ``double``
        - 5
        - IR相机畸变系数 [k1, k2, p1, p2, k3]
      * - ``R_left``
        - ``double``
        - 9
        - IR相机旋转矩阵 (3×3)
      * - ``alpha_c_left``
        - ``double``
        - 1
        - IR相机倾斜系数
      * - **RGB相机参数**
        - 
        - 
        - 
      * - ``fc_right``
        - ``double``
        - 2
        - RGB相机焦距 (fx, fy)
      * - ``cc_right``
        - ``double``
        - 2
        - RGB相机主点坐标 (cx, cy)
      * - ``kc_right``
        - ``double``
        - 5
        - RGB相机畸变系数 [k1, k2, p1, p2, k3]
      * - ``R_right``
        - ``double``
        - 9
        - RGB相机旋转矩阵 (3×3)
      * - ``alpha_c_right``
        - ``double``
        - 1
        - RGB相机倾斜系数
      * - **新标定参数**
        - 
        - 
        - 
      * - ``fc_left_new``
        - ``double``
        - 2
        - IR相机新焦距 (fx, fy)
      * - ``cc_left_new``
        - ``double``
        - 2
        - IR相机新主点坐标 (cx, cy)
      * - ``fc_right_new``
        - ``double``
        - 2
        - RGB相机新焦距 (fx, fy)
      * - ``cc_right_new``
        - ``double``
        - 2
        - RGB相机新主点坐标 (cx, cy)
      * - ``kc_new``
        - ``double``
        - 2
        - 新畸变系数 [k1, k2]
      * - ``R_new``
        - ``double``
        - 9
        - IR到RGB的旋转矩阵 (3×3)
      * - ``T_new``
        - ``double``
        - 3
        - IR到RGB的平移向量 (tx, ty, tz)
图像类型
--------------------
.. c:type:: cloudType

   点云数据类型枚举，定义不同的数据输出格式。
   
   .. list-table:: 枚举值说明
      :widths: 25 75
      :header-rows: 1
      
      * - 枚举值
        - 描述
      * - ``CLOUD``
        - 完整的点云数据 (包含X,Y,Z坐标)
      * - ``CLOUD_X``
        - 仅X坐标数据
      * - ``CLOUD_Y``
        - 仅Y坐标数据
      * - ``CLOUD_Z``
        - 仅Z坐标数据
      * - ``GRAY``
        - 灰度图像数据
      * - ``GRAY_RAW``
        - 原始灰度图像数据
数据类型
--------------------
.. c:type:: dtu_type_t

   DTU（数据发送单元）数据类型枚举。
   
   .. list-table:: 枚举值说明
      :widths: 25 25 50
      :header-rows: 1
      
      * - 枚举值
        - 十六进制值
        - 描述
      * - ``DTU_FRAME_RAW``
        - ``0x0000``
        - 初始图像（原始数据）
      * - ``DTU_FRAME_MAP``
        - ``0x0001``
        - 点云图
      * - ``DTU_FRAME_NULL``
        - ``0x0002``
        - 空帧类型
      * - ``DTU_FRAME_STRIPE``
        - ``0x0003``
        - 条纹图像