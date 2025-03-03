# MAASochist: Multiplatform Power Driver for MAAS via Webhooks

**MAASochist** is a multiplatform power driver implementation for Canonical's MAAS (Metal as a Service) that leverages webhooks to provide power control for consumer hardware or systems with unsupported power drivers. This repository aims to bridge the gap between MAAS and devices that lack native IPMI, iLO, or other hardware-based power management capabilities.

## Why MAASochist?

Canonical MAAS excels at managing physical servers, but its power driver support is primarily focused on enterprise-grade hardware with dedicated management interfaces. This can be a significant hurdle when:

* **Using Consumer Hardware:** Many consumer-grade motherboards and systems lack IPMI or similar remote management features.
* **Dealing with Unsupported Power Drivers:** Some hardware might have proprietary or less common power management solutions not directly supported by MAAS.
* **Testing and Development Environments:** You might want to manage virtual machines or other non-standard hardware through MAAS for testing and development purposes.

MAASochist addresses these limitations by providing a flexible, webhook-based power driver. This allows you to:

* **Control Power via Scripts:** Execute custom scripts or commands to power on, power off, or reboot your devices.
* **Integrate with Existing Systems:** Integrate with existing home automation systems, smart plugs, or other network-controllable devices for power management.
* **Extend MAAS Capabilities:** Expand the range of hardware manageable by MAAS beyond traditional server infrastructure.

## How it Works

MAASochist utilizes MAAS webhooks to trigger external scripts or services when power actions are requested. When MAAS attempts to power on, off, or reboot a machine, it sends a webhook request to a configurable endpoint. This endpoint, in turn, executes the necessary commands to control the device's power state.

## Limitations of Software Power Drivers

While MAASochist offers a flexible solution, it's essential to understand the limitations of software-based power drivers compared to hardware-based ones:

* **Reliance on Network Connectivity:** Software power drivers require network connectivity to function. If the network is down, power control is unavailable. Hardware power drivers, such as IPMI, often have dedicated network interfaces.
* **Operating System Dependency:** Software power drivers typically rely on the operating system being running on the target machine. If the OS is crashed or unresponsive, power control might be impossible. Hardware power drivers operate independently of the OS.
* **Security Considerations:** Exposing power control via webhooks introduces potential security risks. It's crucial to implement proper authentication and authorization mechanisms.
* **Latency:** Software power drivers might introduce latency due to network communication and script execution. Hardware power drivers are typically faster and more responsive.
* **Less reliable for hard resets:** Software power drivers might not be able to perform a true hard reset in all circumstances, especially if the OS is in a completely hung state. Hardware based power drivers are designed to perform these actions.

## MAAS Power Driver Documentation

For more information on MAAS power drivers, refer to the official documentation:

* [MAAS Power Drivers Reference](https://maas.io/docs/reference-power-drivers)

## Getting Started

1.  **Clone the Repository:**
    ```bash
    git clone [repository URL]
    ```
2.  **Configure Webhooks:** Configure MAAS to send webhooks to your MAASochist endpoint.
3.  **Implement Power Control Scripts:** Create scripts or commands to control the power state of your target devices.
4.  **Deploy and Test:** Deploy MAASochist and test power control functionality.

## Contributing

Contributions are welcome! If you have ideas for improvements or bug fixes, please submit a pull request.
