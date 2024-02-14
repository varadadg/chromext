import React, { useState } from "react";
import AdminTab from "./AdminTab";

const CircularMenu = () => {
  const [isOpen, setIsOpen] = useState(false);
  const [showAdminTab, setShowAdminTab] = useState(false);

  const toggleMenu = () => {
    setIsOpen(!isOpen);
  };

  const showAdmin = () => {
    setShowAdminTab(true);
  };

  const handleDragStart = (event) => {
    event.dataTransfer.setData("text/plain", event.target.id);
  };

  const handleDragOver = (event) => {
    event.preventDefault();
  };

  const handleDrop = (event) => {
    event.preventDefault();
    const data = event.dataTransfer.getData("text/plain");
    console.log("Dropped element:", data);
  };

  return (
    <div
      style={{
        display: "flex",
        alignItems: "center",
        justifyContent: "center",
        height: "100vh",
        position: "relative",
      }}
      onDragOver={handleDragOver}
      onDrop={handleDrop}>
      <div style={{ position: "relative" }}>
        <button
          style={{
            height: "80px",
            width: "80px",
            backgroundColor: "#1a202c",
            color: "#fff",
            fontWeight: "bold",
            borderRadius: "50%",
            display: "flex",
            alignItems: "center",
            justifyContent: "center",
            position: "absolute",
            cursor: "pointer",
          }}
          onMouseEnter={toggleMenu}
          onDragStart={handleDragStart}
          draggable={true}>
          {isOpen ? "opened" : "closed"}
        </button>
        {isOpen && (
          <div style={{ position: "absolute", top: 0, right: 0 }}>
            <button
              onClick={showAdmin}
              style={{
                height: "64px",
                width: "64px",
                backgroundColor: "#4c51bf",
                color: "#fff",
                fontWeight: "bold",
                borderRadius: "50%",
                display: "flex",
                alignItems: "center",
                justifyContent: "center",
                position: "absolute",
                cursor: "pointer",
                top: 0,
                right: 0,
              }}
              onDragStart={handleDragStart}
              draggable={true}>
              Admin
            </button>
            <button
              style={{
                height: "48px",
                width: "48px",
                backgroundColor: "#4c51bf",
                color: "#fff",
                fontWeight: "bold",
                borderRadius: "50%",
                display: "flex",
                alignItems: "center",
                justifyContent: "center",
                position: "absolute",
                cursor: "pointer",
                top: 0,
                left: "80px",
              }}
              onDragStart={handleDragStart}
              draggable={true}>
              User
            </button>
            <button
              style={{
                height: "48px",
                width: "48px",
                backgroundColor: "#4c51bf",
                color: "#fff",
                fontWeight: "bold",
                borderRadius: "50%",
                display: "flex",
                alignItems: "center",
                justifyContent: "center",
                position: "absolute",
                cursor: "pointer",
                top: "80px",
                right: 0,
              }}
              onDragStart={handleDragStart}
              draggable={true}>
              3
            </button>
            <button
              style={{
                height: "48px",
                width: "48px",
                backgroundColor: "#4c51bf",
                color: "#fff",
                fontWeight: "bold",
                borderRadius: "50%",
                display: "flex",
                alignItems: "center",
                justifyContent: "center",
                position: "absolute",
                cursor: "pointer",
                bottom: 0,
                left: 0,
              }}
              onDragStart={handleDragStart}
              draggable={true}>
              4
            </button>
          </div>
        )}
      </div>
      {showAdminTab && (
        <div
          style={{
            position: "absolute",
            top: 0,
            left: "100%",
            marginLeft: "4px",
          }}>
          <AdminTab />
        </div>
      )}
    </div>
  );
};

export default CircularMenu;
